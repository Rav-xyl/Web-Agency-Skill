# Deployment Reference

## Platform-Specific Recipes

### Vercel (Next.js / React / SvelteKit / Astro)
```bash
# Install CLI
npm i -g vercel

# First deploy (interactive setup)
vercel

# Deploy to production
vercel --prod

# Set env vars via CLI
vercel env add NEXT_PUBLIC_API_URL production

# Rollback: use Vercel dashboard → Deployments → select previous → Promote to Production

# Preview URLs: every git push creates a preview URL automatically
```

**Checklist:**
- [ ] `vercel.json` configured for headers, redirects, rewrites
- [ ] Env vars set in Vercel dashboard (not just local .env)
- [ ] Custom domain added and SSL auto-provisioned
- [ ] Analytics enabled in Vercel dashboard

### Netlify (Static / JAMstack / Gatsby / Hugo / Astro)
```bash
# Install CLI
npm i -g netlify-cli

# Login
netlify login

# First deploy
netlify init

# Deploy to production
netlify deploy --prod

# Set env vars
netlify env:set MY_VAR my_value

# Rollback: Netlify dashboard → Deploys → select previous → Publish deploy
```

**Netlify `netlify.toml` example:**
```toml
[build]
  command = "npm run build"
  publish = "dist"

[[redirects]]
  from = "/old-page"
  to = "/new-page"
  status = 301

[[headers]]
  for = "/*"
  [headers.values]
    X-Frame-Options = "SAMEORIGIN"
    X-Content-Type-Options = "nosniff"
    Strict-Transport-Security = "max-age=63072000; includeSubDomains; preload"
```

### Railway (Node.js / Python / Docker apps)
```bash
# Install CLI
npm i -g @railway/cli

# Login and link
railway login
railway init

# Deploy
railway up

# View logs
railway logs

# Set env vars
railway env set MY_VAR=my_value
```

### DigitalOcean / Hetzner VPS (Ubuntu)
```bash
# Initial server setup
ssh root@your_server_ip

# Create non-root user
adduser deploy
usermod -aG sudo deploy
su - deploy

# Install Node.js (via nvm)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
nvm install --lts
nvm use --lts

# Install PM2 (process manager)
npm i -g pm2

# Clone repo and install
git clone https://github.com/your/repo.git /var/www/yoursite
cd /var/www/yoursite
npm install
npm run build

# Start with PM2
pm2 start npm --name "yoursite" -- start
pm2 startup
pm2 save

# Install Nginx
sudo apt install nginx

# Nginx config
sudo nano /etc/nginx/sites-available/yoursite
```

**Nginx config:**
```nginx
server {
    server_name yoursite.com www.yoursite.com;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_cache_bypass $http_upgrade;
    }

    # Security headers
    add_header Strict-Transport-Security "max-age=63072000; includeSubDomains; preload" always;
    add_header X-Frame-Options "SAMEORIGIN" always;
    add_header X-Content-Type-Options "nosniff" always;
    add_header Referrer-Policy "strict-origin-when-cross-origin" always;
}
```

```bash
# Enable site
sudo ln -s /etc/nginx/sites-available/yoursite /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx

# SSL with Certbot
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx -d yoursite.com -d www.yoursite.com
# Certbot auto-renews via systemd timer — verify with:
sudo certbot renew --dry-run
```

### WordPress (Kinsta / WP Engine / Hostinger cPanel)
```bash
# Deploy via WP-CLI
wp core update
wp plugin update --all
wp theme update --all

# Backup before any update
wp db export backup-$(date +%Y%m%d).sql
tar -czf files-backup-$(date +%Y%m%d).tar.gz wp-content/

# Migrate between environments
wp search-replace 'staging.yoursite.com' 'yoursite.com' --all-tables
wp cache flush
```

---

## DNS Configuration Reference

### Standard DNS Records
```
Type  | Name          | Value                    | TTL
------|---------------|--------------------------|------
A     | @             | [server IP]              | 3600
A     | www           | [server IP]              | 3600
CNAME | www           | yoursite.com             | 3600  (use A or CNAME, not both)
MX    | @             | mail.yoursite.com        | 3600
TXT   | @             | v=spf1 include:... ~all  | 3600
```

### For Vercel
```
A     | @   | 76.76.21.21       | auto
CNAME | www | cname.vercel-dns.com | auto
```

### For Netlify
```
A     | @   | 75.2.60.5         | auto
CNAME | www | [yoursite].netlify.app | auto
```

### For Cloudflare (recommended for all projects — free CDN + DNS)
1. Add site to Cloudflare (free)
2. Update nameservers at registrar to Cloudflare nameservers
3. Wait up to 48h for propagation
4. Enable "Proxied" (orange cloud) on A and CNAME records for CDN + DDoS protection
5. Set SSL/TLS to "Full (strict)" in Cloudflare dashboard

---

## CI/CD — GitHub Actions (scores 16+)

```yaml
# .github/workflows/deploy.yml
name: Deploy to Production

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'

      - name: Install dependencies
        run: npm ci

      - name: Run tests
        run: npm test

      - name: Build
        run: npm run build
        env:
          NEXT_PUBLIC_API_URL: ${{ secrets.NEXT_PUBLIC_API_URL }}

      - name: Deploy to Vercel
        uses: amondnet/vercel-action@v25
        with:
          vercel-token: ${{ secrets.VERCEL_TOKEN }}
          vercel-org-id: ${{ secrets.VERCEL_ORG_ID }}
          vercel-project-id: ${{ secrets.VERCEL_PROJECT_ID }}
          vercel-args: '--prod'
```

---

## Redirect Map Template

Use this spreadsheet to track all URL redirects when launching a new site over an existing one.

```
OLD URL                          | NEW URL                    | STATUS | TYPE
---------------------------------|----------------------------|--------|-----
/about-us                        | /about                     | 301    | permanent
/services/web-design             | /services/websites         | 301    | permanent
/blog/2022/old-post-title        | /blog/new-post-title       | 301    | permanent
/contact-us                      | /contact                   | 301    | permanent
/products                        | /services                  | 301    | permanent
/old-page-that-no-longer-exists  | /                          | 301    | permanent (to homepage)
```

**In Next.js (`next.config.js`):**
```js
module.exports = {
  async redirects() {
    return [
      { source: '/about-us', destination: '/about', permanent: true },
      { source: '/contact-us', destination: '/contact', permanent: true },
      // ... add all from your redirect map
    ];
  },
};
```

**In Nginx:**
```nginx
rewrite ^/about-us$ /about permanent;
rewrite ^/contact-us$ /contact permanent;
```

---

## Post-Deploy Verification Commands

```bash
# Check site is live and returning 200
curl -I https://yoursite.com/

# Check redirect is working
curl -I https://yoursite.com/old-url

# Check SSL
curl -I https://yoursite.com/ | grep -i strict-transport

# Check all pages for 404s (install linkchecker first)
pip install linkchecker
linkchecker https://yoursite.com/

# Check sitemap
curl https://yoursite.com/sitemap.xml | grep '<url>' | wc -l

# Submit sitemap to Google (via Search Console API or manually)
# Go to: Google Search Console → Sitemaps → Add a new sitemap
```
