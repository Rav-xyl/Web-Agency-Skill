# Security Reference

## HTTP Security Headers

### Next.js — next.config.js
```js
const securityHeaders = [
  { key: 'Strict-Transport-Security', value: 'max-age=63072000; includeSubDomains; preload' },
  { key: 'X-Frame-Options', value: 'SAMEORIGIN' },
  { key: 'X-Content-Type-Options', value: 'nosniff' },
  { key: 'Referrer-Policy', value: 'strict-origin-when-cross-origin' },
  { key: 'Permissions-Policy', value: 'camera=(), microphone=(), geolocation=()' },
  {
    key: 'Content-Security-Policy',
    value: [
      "default-src 'self'",
      "script-src 'self' 'unsafe-inline' https://www.googletagmanager.com",
      "style-src 'self' 'unsafe-inline'",
      "img-src 'self' data: https:",
      "font-src 'self'",
      "connect-src 'self' https://www.google-analytics.com",
    ].join('; ')
  },
];

module.exports = {
  async headers() {
    return [{ source: '/(.*)', headers: securityHeaders }];
  },
};
```

### Nginx
```nginx
add_header Strict-Transport-Security "max-age=63072000; includeSubDomains; preload" always;
add_header X-Frame-Options "SAMEORIGIN" always;
add_header X-Content-Type-Options "nosniff" always;
add_header Referrer-Policy "strict-origin-when-cross-origin" always;
add_header Permissions-Policy "camera=(), microphone=(), geolocation=()" always;
add_header Content-Security-Policy "default-src 'self'; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline'; img-src 'self' data: https:;" always;
```

### .htaccess (Apache)
```apache
Header always set Strict-Transport-Security "max-age=63072000; includeSubDomains; preload"
Header always set X-Frame-Options "SAMEORIGIN"
Header always set X-Content-Type-Options "nosniff"
Header always set Referrer-Policy "strict-origin-when-cross-origin"
Header always set Permissions-Policy "camera=(), microphone=(), geolocation=()"
```

---

## Audit Commands

```bash
# Check npm vulnerabilities
npm audit --audit-level=high

# Fix automatically where possible
npm audit fix

# Check git history for accidentally committed secrets
git log --all --full-history -- "*.env"
git log -p --all | grep -i "secret\|password\|api_key\|token"

# Scan for secrets in codebase (install: https://github.com/trufflesecurity/trufflehog)
trufflehog filesystem ./

# Check open ports on VPS
nmap -sV yoursite.com

# SSL test (run in browser or curl)
curl -I https://yoursite.com

# Rate limiting test (basic)
ab -n 100 -c 20 https://yoursite.com/api/contact
```

---

## Online Security Scanners
- Mozilla Observatory: https://observatory.mozilla.org — target: A or A+
- SSL Labs: https://ssllabs.com/ssltest — target: A+
- Security Headers: https://securityheaders.com — target: A+
- HSTS Preload: https://hstspreload.org

---

## OWASP Top 10 Checklist

| # | Risk | Check |
|---|------|-------|
| A01 | Broken Access Control | Users can't access other users' data. Admin routes protected. |
| A02 | Cryptographic Failures | No plaintext passwords. HTTPS everywhere. Secrets in env vars. |
| A03 | Injection | All DB queries parameterised. No raw SQL from user input. |
| A04 | Insecure Design | Rate limiting on forms/auth. No open redirects. |
| A05 | Security Misconfiguration | No default passwords. Error pages don't expose stack traces. |
| A06 | Vulnerable Components | `npm audit` clean. Dependencies up to date. |
| A07 | Auth Failures | Passwords hashed (bcrypt/argon2). Session timeout. 2FA available. |
| A08 | Data Integrity Failures | Signed JWTs. Package integrity checks. |
| A09 | Logging Failures | Errors logged (Sentry). No sensitive data in logs. |
| A10 | SSRF | No user-controlled URLs fetched server-side without allowlist. |

---

## Rate Limiting Examples

### Next.js API Routes (using upstash/ratelimit)
```js
import { Ratelimit } from '@upstash/ratelimit';
import { Redis } from '@upstash/redis';

const ratelimit = new Ratelimit({
  redis: Redis.fromEnv(),
  limiter: Ratelimit.slidingWindow(10, '60 s'), // 10 requests per 60 seconds
});

export default async function handler(req, res) {
  const { success } = await ratelimit.limit(req.headers['x-forwarded-for'] ?? 'anonymous');
  if (!success) return res.status(429).json({ error: 'Too many requests' });
  // ... rest of handler
}
```

### Express / Node.js
```js
const rateLimit = require('express-rate-limit');
const limiter = rateLimit({ windowMs: 60 * 1000, max: 10 });
app.use('/api/contact', limiter);
```

---

## Input Sanitisation

```js
// Never trust client input — always validate server-side
import { z } from 'zod';

const contactSchema = z.object({
  name: z.string().min(1).max(100),
  email: z.string().email(),
  message: z.string().min(10).max(2000),
});

// In your API handler:
const result = contactSchema.safeParse(req.body);
if (!result.success) return res.status(400).json({ error: 'Invalid input' });
```

---

## Environment Variable Checklist

```bash
# .env.example (commit this — no real values)
DATABASE_URL=
STRIPE_SECRET_KEY=
SENDGRID_API_KEY=
NEXTAUTH_SECRET=
NEXTAUTH_URL=

# .gitignore (always include these)
.env
.env.local
.env.production
.env.*.local
```

Never hardcode any key, token, or secret in source code.
Use platform secrets vaults: Vercel Environment Variables, Netlify Environment Variables, Railway Variables, AWS Secrets Manager.
