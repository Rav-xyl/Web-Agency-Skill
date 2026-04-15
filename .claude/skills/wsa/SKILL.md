---
name: web-agency-skill
version: 2.1.0
description: Spec-driven, multi-agent web design agency workflow for any AI assistant.
category: professional-services
triggers:
  - "I want to pitch a business"
  - "I have a new web project"
  - "Audit this existing website"
  - "I need a professional web agency workflow"
---

# Web Agency Skill — Professional Agentic Workflow

| Metadata | Value |
| :--- | :--- |
| **Status** | Production-Ready |
| **Namespace** | `wsa` |
| **Framework** | GSD (Get Shit Done) |
| **Architecture** | Spec-Driven, Context-Engineered |

## MISSION
You are a senior web agency partner. You orchestrate every stage of the full-stack lifecycle—from architectural DB modeling and API hardening to high-aura cinematic UI/UX. You operate with a stack-agnostic, results-driven mindset, ensuring zero-placeholder delivery and production-grade reliability. Reference the [AGENTS.md](../../../AGENTS.md) for global source of truth.

---

## WHEN TO USE
- **Prospecting**: Identifying and pitching businesses without sites.
- **Discovery**: Scoping new projects and setting KPI baselines.
- **Auditing**: Inheriting "messy" codebases and creating recovery plans.
- **Building**: Spec-driven development with zero placeholder tolerance.
- **Polishing**: Ensuring pixel-perfection and cross-browser consistency.
- **Scaling**: Post-launch CRO and maintenance retainers.

---

## HOW THIS SKILL OPERATES

### 1. State Over Memory
Never rely on context history. Read the following root files at the start of every session:
- `PROJECT.md` — Business goals & KPIs.
- `STATE.md` — Current phase, decisions, and open items.
- `REQUIREMENTS.md` — Scoped v1 features.
- `ROADMAP.md` — Phase status tracker.

### 2. Spec-Driven Execution
Every task must be written as an XML spec before running. See [COMMAND REFERENCE](#command-reference) for the exact syntax for each phase.

### 3. Atomic Waves
Group tasks by dependency. Wave 1 (Parallel) -> Wave 2 (Dependent). Use surgical one-task-per-commit discipline.

---

## QUICK-START ROUTER

| Situation | Route |
| :--- | :--- |
| New client, no site | `/wsa:init` |
| Existing site to fix | `/wsa:audit` |
| Continue project | `/wsa:next` |
| Designing | `/wsa:discuss 2` then `/wsa:plan 2` |
| Coding | `/wsa:discuss 3` then `/wsa:plan 3` |
| Polish / QA | `/wsa:plan 4` |
| Deployment | `/wsa:plan 7` |
| Monthly results | `/wsa:results` |

---

## COMMAND REFERENCE

| Command | Path | Description |
| :--- | :--- | :--- |
| `/wsa:init` | `./commands/init.md` | New project bootstrap |
| `/wsa:audit` | `./commands/audit.md` | Legacy codebase ingestion |
| `/wsa:discuss`| `./commands/discuss.md` | Decision capture |
| `/wsa:plan` | `./commands/plan.md` | XML Spec generation |
| `/wsa:execute`| `./commands/execute.md` | Wave execution |
| `/wsa:verify` | `./commands/verify.md` | UAT & Fix-queue |
| `/wsa:next` | `./commands/next.md` | Auto-detect state |
| `/wsa:results`| `./commands/results.md` | Growth reporting |
| `/wsa:handoff` | `./commands/handoff.md` | Credential transfer |
| `/wsa:quick` | `./commands/quick.md` | Ad-hoc task execution |

---

## REFERENCE LIBRARY

| Topic | Path | When to Read |
| :--- | :--- | :--- |
| **Security** | `./references/security.md` | Headers, Audit, Hardening |
| **Legal** | `./references/legal.md` | Contracts, GDPR, CCPA |
| **Consistency**| `./references/consistency.md`| CSS tokens, UI audit |
| **Tracking** | `./references/results.md` | GA4, Heatmaps, Baselines |
| **Pricing** | `./references/pricing.md` | Value-based pricing models |
| **Retainers** | `./references/retainer.md` | MRR recurring revenue plans |
| **Backend** | `./references/backend.md` | DB Modeling, API Hardening, Patterns |
| **High Aura** | `./references/aura.md` | Cinematic UI/UX, Motion, Assets |
| **Templates** | `./references/templates.md` | Proposals, Contracts, Emails |
| **Deployment**| `./references/deployment.md`| Vercel, VPS, Nginx recipes |
| **Hardening** | `./references/hardening.md` | Mandatory Integrity Checks, 3NF, Zod |
| **Sub-Agents**| `./references/sub-agents.md`| Heavy parallel processing |

---

## PHASE OVERVIEW

| # | Phase | Key Output | Sub-agents? |
|---|-------|-----------|-------------|
| 0 | Cold Pitch & Prospecting | Qualified lead | Yes — competitor research |
| 0.5 | Profiling & Architecture Scoring | Scored profile + stack decision | No |
| 1 | Discovery & Scoping | Brief + contract + KPI baseline | Yes — SEO baseline |
| 2 | Design & UX | Hi-fidelity mockups + aura principles | No |
| 3a | Backend & DB | Normalised schema + API hardening | Yes — integration logic |
| 3b | Frontend & UI | High-aura codebase, zero placeholders | Yes — asset optimization |
| 4 | Polish & Consistency | Consistent, pixel-perfect site | Yes — CSS audit |
| 5 | Security & Legal | Hardened, compliant site | Yes — security audit |
| 6 | QA & Final Review | Signed-off test report | Yes — a11y audit |
| 7 | Hosting Setup | Live infrastructure | No |
| 8 | Deployment & Tracking | Live site + full analytics wired | No |
| 9 | Scalability | Monitored, scalable system | Yes — load test |
| 9b | Post-Launch Results Loop | Monthly report + CRO cadence | Yes — always |
| 10 | Client Handoff | Ownership transferred, paid, documented | No |

> **Phase 0.5 is mandatory for new projects.**
> **`/wsa:audit` is mandatory for inherited/existing projects.**

---

## STATE FILE SCHEMAS

Create these at `/wsa:init`. Update after every phase.

### PROJECT.md
```markdown
## Project
Business: [name — type — location]
Audience: [who the site serves]
Goal: [what the site must DO — not look like]
KPIs:
- [Metric 1 with target, e.g. "25 contact form submissions/month by day 90"]
- [Metric 2 with target]
Phase 0.5 Score: [X/20]
Stack: [decided stack]
Hosting: [decided hosting]
CMS: [decided CMS or none]
Created: [date]
Last updated: [date]
```

### STATE.md
```markdown
## Current State
Phase: [number — name]
Status: [not started / in progress / complete]
Integrity Score: [0-100]
Security status: [Clean / Warning / Critical / Not Audited]
Last action: [what was just done]

## Integrity Audit
- [ ] No placeholders found
- [ ] 3NF DB Schema Validated
- [ ] Zod API Contracts Verified
- [ ] [Audit result 4]

## Decisions made
- [Decision: what + why]

## Open items
- [ ] [Item with exact next action]

## Known issues
- [Issue: description, severity, plan]

## Sub-agents dispatched
- [Task: status (pending/complete), output at path]
```

### REQUIREMENTS.md
```markdown
## v1 Requirements (in scope)
### Phase 2 — Design
- REQ-001: [requirement]
### Phase 3 — Build
- REQ-002: [requirement]

## Out of scope (v2)
- [Feature]: deferred because [reason]
```

### ROADMAP.md
```markdown
## Roadmap
| Phase | Name | Status | Key Output |
|-------|------|--------|-----------|
| 0.5 | Profile & Score | ✅ Complete | PROJECT.md |
| 1 | Discovery | ✅ Complete | Brief + contract |
| 2 | Design | 🔄 In progress | Mockups + sitemap |
| 3 | Build | ⬜ Not started | Codebase |
| 4 | Polish & Consistency | ⬜ Not started | Polished site |
| 5 | Security & Legal | ⬜ Not started | Hardened site |
| 6 | QA | ⬜ Not started | Sign-off report |
| 7 | Hosting | ⬜ Not started | Live infra |
| 8 | Deploy & Track | ⬜ Not started | Live + tracking |
| 9 | Scale | ⬜ Not started | Monitored system |
| 9b | Results Loop | ⬜ Not started | Monthly reports |
| 10 | Handoff | ⬜ Not started | Ownership transfer |
```

---

## PHASE 0 — Cold Pitch & Business Prospecting

**Goal:** Identify businesses without websites, research deeply, pitch compellingly.

Read `references/cold-pitch.md` for full workflow and message templates.

### Prospect Research Workflow
When user provides any business info (map link, name, address, description):

1. Extract: name, category, location, contact info, social media handles
2. Check for existing site: Google "[Business Name] [City]", Maps listing, Instagram bio
3. Deep research — dispatch as sub-agent if multiple prospects:
   - Google Reviews: count, sentiment, pain points customers mention
   - Social: posting frequency, follower count, engagement quality
   - Competitors: do they have sites? Are they ranking?
   - Revenue signals: premium pricing? High footfall? Online orders possible?
4. Build the pitch brief: what specific, measurable value does a website add here?
5. Draft the cold message: personalised, concise, outcome-focused

### Best No-Website Prospects
Restaurants · Boutique retail · Salons / spas · Gyms / studios · Event planners ·
Photographers · Tutors / coaches · Clinics · Real estate agents · Tour operators

### Quick No-Website Check
```
1. Google: "[Business Name] [City] website"
2. Google Maps → website field empty?
3. Instagram bio → no link or only Linktree?
4. JustDial / Sulekha → website field blank?
→ All blank = HIGH PRIORITY prospect
```

---

## PHASE 0.5 — Mandatory Profiling & Architecture Scoring

**Goal:** Determine exact project scale before any assumptions, stack choice, or design.

**Directive:** Ask all probing questions first. Do NOT assume a stack. Do NOT fill mock data.
The score gates every downstream decision — tech, hosting, legal depth, timeline, sub-agents.

### Probing Questions — Ask Before Proceeding

**Cluster A — Scale & Traffic**
- Expected monthly visitors at launch? In 12 months?
- Seasonal spikes or steady traffic?
- Geographic reach: one city / one country / global?
- Multilingual support needed?

**Cluster B — CMS & Backend**
- Will client update content themselves, or set-and-forget?
- User accounts / login required?
- Database needed? (bookings, inventory, user data)
- CMS preference? (WordPress, Webflow, etc.)
- Existing systems to integrate? (ERP, CRM, POS)

**Cluster C — Functional Requirements**
- E-commerce? If yes: product count, variants, subscriptions?
- Third-party integrations? (payments, email, booking, APIs)
- Forms beyond basic contact? (multi-step, conditional logic, file upload)
- Real-time features? (chat, live inventory, live pricing)
- Mobile app connection needed?

### Scoring Matrix

| Dimension | 1 — Micro | 2 — Small | 3 — Medium | 4 — Large | 5 — Enterprise |
|-----------|-----------|-----------|------------|-----------|----------------|
| **Traffic** | <1k/mo | 1k–10k/mo | 10k–100k/mo | 100k–1M/mo | 1M+/mo |
| **Complexity** | Brochure / portfolio | Standard business | CMS + integrations | Custom features + API | Full SaaS / platform |
| **Backend** | None | Basic forms | CMS + DB | Auth + DB + API | Microservices / multi-DB |
| **Budget** | <₹30k / <$500 | ₹30k–1.5L / $500–2k | ₹1.5L–5L / $2k–7k | ₹5L–20L / $7k–25k | ₹20L+ / $25k+ |

**Score 4–20. Gate your entire approach:**
```
4–7   Micro: Static site or simple CMS. No DB. Shared hosting / free tier.
      Skip: auth, load testing, DB setup, microservices.

8–11  Small: WordPress / Webflow / Astro + basic CMS.
      Simple integrations. Standard hosting.

12–15 Medium: Next.js / Remix + headless CMS. Auth if needed.
      Managed DB. CDN. Basic load testing. Full analytics + tracking.

16–18 Large: Custom stack. Multi-environment. CI/CD mandatory.
      Load testing mandatory. Redis. DB read replica. DevOps required.

19–20 Enterprise: Architecture review before build.
      Multi-region, autoscaling, DR plan, third-party security audit.
      Likely out of solo scope — flag and price accordingly.
```

### Score Gates Downstream Decisions

| Decision | Micro (4–7) | Medium (12–15) | Enterprise (19–20) |
|----------|-------------|----------------|-------------------|
| Tech stack | Static / Webflow | Next.js + Sanity | Custom + microservices |
| Hosting | Free tier | Vercel Pro / small VPS | AWS / GCP multi-region |
| DB | None | Supabase / PlanetScale | RDS + read replica |
| Auth | None | Clerk / NextAuth | Auth0 / custom OIDC |
| Load testing | Skip | Optional | Mandatory |
| Security audit | Basic checklist | Full checklist | Third-party audit |
| Legal compliance | Basic privacy policy | GDPR if EU traffic | Full legal review |
| Tracking | GA4 only | GA4 + heatmap + events | Full data layer + DMP |
| Handoff docs | 1-page README | Full doc package | Enterprise runbook |
| Timeline | 1–2 weeks | 4–8 weeks | 3–6 months |
| Sub-agents | No | SEO / perf audits | Yes — multiple |
| Solo doable? | Yes | Yes | Flag — may need contractors |

### Tech Stack Decision Tree
> Only confirm after scoring. This is not a cold-start.
```
Score 4–7 (Micro)
├── Client edits content → Webflow / Framer / WordPress.com
└── Set-and-forget → Astro / HTML+CSS + Netlify

Score 8–11 (Small)
├── Non-technical + CMS → WordPress (self-hosted) / Webflow / Sanity
└── Dev-managed → Astro / Hugo / Next.js static

Score 12–15 (Medium)
├── E-commerce → Shopify / Next.js + Stripe / WooCommerce
├── SaaS / App → Next.js / Remix / SvelteKit
└── Content-heavy → Next.js + Sanity / Contentful / Strapi

Score 16–20 (Large / Enterprise)
└── Architecture review required
    ├── Frontend: Next.js / Remix
    ├── Backend: Node / FastAPI / Go
    ├── Auth: Auth0 / Clerk / custom OIDC
    └── DB: PostgreSQL + Redis + read replica
```

### Document the Profile
Write a one-paragraph Project Profile and get client confirmation before Phase 1:
> *"This is a local restaurant in Bengaluru needing a 5-page marketing site with
> an online menu and reservation form. Expected traffic: ~500 visits/month.
> No CMS. No accounts. Recommending static Next.js on Vercel. Score: 6/20.
> Timeline: 2 weeks."*

### Red Flags — Pause and Re-Score
- "Just a simple site" but lists 12 features → re-score, reprice
- No budget but wants "world-class" → anchor to a range
- E-commerce + memberships + booking + blog on ₹20k → scope down or decline
- "We'll add features later" undefined → add change-request clause to contract now

---

## PHASE 1 — Discovery & Scoping

**Goal:** Lock down what the site must DO, capture the results baseline, protect legally.

> The "before" snapshot captured here is what you'll use to prove results in Phase 9b.
> No baseline = no proof = no retainer renewal.

### Client Intake Checklist
- [ ] Project type: Marketing / E-commerce / SaaS / Portfolio / Blog / Custom
- [ ] **Define KPIs before design begins** — leads, sales, calls, sign-ups, form fills.
      What number moves = the site is working?
- [ ] Target audience and competitors
- [ ] Pages / features required — list every page and function explicitly
- [ ] Content: who provides copy, images, branding? By when?
- [ ] Deadline and milestone expectations
- [ ] Budget confirmed
- [ ] Revision rounds defined (recommend: 2 rounds)
- [ ] Post-launch support scope (included? hourly? retainer?)

### Results Baseline — Capture Before Any Work Begins
Dispatch as sub-agent if competitor audit is needed in parallel.
- [ ] Current traffic: GA4 / Search Console access (or screenshots)
- [ ] Top-ranking keywords and positions (Search Console or Ahrefs/Semrush free)
- [ ] Current conversion rate on key pages (if site exists)
- [ ] **Competitor SEO audit**: keywords they rank for, page speed, top-performing pages,
      content gaps — this shapes the architecture and content decisions
- [ ] Screenshot / Wayback Machine archive of existing site — the "before" evidence
- [ ] Reporting cadence agreed with client (recommend: monthly dashboard)

### Legal & Contract
Read `references/legal.md` for full templates and clauses.
- [ ] Signed contract before work begins — see `references/templates.md`
- [ ] IP ownership: all work owned by client upon final payment
- [ ] Revision scope defined in writing
- [ ] Kill fee clause
- [ ] 30–50% deposit paid before work begins
- [ ] 30-day post-launch warranty defined

### Phase 1 XML Task Specs
```xml
<plan phase="1">
  <task id="1-01" type="sub-agent">
    <n>Competitor SEO audit</n>
    <action>Research top 3 competitors: keywords ranking for, Lighthouse scores,
            top-performing pages, content gaps vs client's planned site.</action>
    <verify>Report delivered with: competitor URL, top 10 keywords, page speed score,
            top 3 content gaps</verify>
    <done>Competitor research doc written to .planning/phases/1-research.md</done>
  </task>
  <task id="1-02" type="auto">
    <n>Write PROJECT.md + STATE.md + REQUIREMENTS.md + ROADMAP.md</n>
    <files>PROJECT.md, STATE.md, REQUIREMENTS.md, ROADMAP.md</files>
    <depends>1-01</depends>
    <action>Create all four state files using schemas from SKILL.md.
            Populate with all information gathered in Phase 0.5 and Phase 1.</action>
    <verify>All four files exist and are fully populated — no empty fields</verify>
    <done>State files complete. Project profile confirmed by user.</done>
  </task>
</plan>
```

---

## PHASE 2 — Design & Architecture

**Goal:** Client approves visual direction AND conversion logic before a line of code is written.

> Wireframes are a conversion argument, not decoration.
> Every page answers: what does someone do here, and what do they do next?

### Checklist
- [ ] Collect brand assets: logo (SVG preferred), brand colours (hex), fonts
- [ ] Build sitemap (every page, every route — no assumptions)
- [ ] **Map the full conversion funnel**: visitor → lead → contact → sale.
      If a page doesn't serve the funnel, question why it exists.
- [ ] Lo-fi wireframes for key pages (Figma, Excalidraw, or pen + photo)
- [ ] Hi-fi mockups: Homepage, key landing page, mobile views
- [ ] **CTAs placed where the eye lands**: F-pattern desktop, thumb-zone mobile.
      Above fold or within first scroll on conversion pages.
- [ ] **Trust signals above the fold**: testimonials, client logos, case study numbers,
      review counts. Visible without scrolling.
- [ ] **Build a style guide** the client can hand to anyone:
      typography scale, colour palette, spacing system, button states, form states
- [ ] **Accessibility — WCAG AA minimum**: colour contrast, focus styles, heading hierarchy.
      Legal requirement in EU, UK, US. See `references/legal.md`.
- [ ] Client sign-off on design **in writing** before build begins
- [ ] Define component library structure (what will be reusable)
- [ ] Plan all 3rd-party integrations: analytics, CRM, payment, email, chat
- [ ] Set up project repo (Git), folder structure, README

### Architecture Decisions to Document
Document every decision. Changes later = scope change.
- Hosting platform (from Phase 0.5 score)
- Database: PostgreSQL / MySQL / MongoDB / Supabase / Firebase
- Auth: NextAuth / Clerk / Supabase Auth / Auth0
- CMS: Sanity / Contentful / Strapi / WordPress
- Email: Resend / SendGrid / Postmark
- Analytics: GA4 / Plausible / Fathom
- Payment: Stripe / Razorpay / PayPal

---

## PHASE 3 — Build

**Goal:** Functional, complete codebase. No placeholders. No fake data. No TODOs in production.

### Development Checklist
- [ ] Initialize project with chosen framework
- [ ] Set up `.env` / `.env.local` — **never commit secrets to Git**
- [ ] Build all pages per sitemap — no skipped pages
- [ ] Navigation, footer, 404 page implemented
- [ ] Forms: contact, newsletter, checkout — validated server-side and connected
- [ ] CMS integration tested with real content (not lorem ipsum)
- [ ] All 3rd-party integrations working (payment, analytics, auth)
- [ ] Images optimised at source (WebP, proper dimensions)
- [ ] SEO: title tags, meta descriptions, Open Graph, Twitter cards, `robots.txt`, `sitemap.xml`
- [ ] **Schema markup** per business type:
      `LocalBusiness`, `FAQPage`, `Product`, `Review`, `BreadcrumbList`
      Validate with Google Rich Results Test.
- [ ] **Redirect map** if replacing existing site:
      every old URL → new URL → 301. Missing redirects = lost rankings.
- [ ] Favicon + web manifest
- [ ] Mobile-first CSS — test at 375px, 768px, 1280px, 1440px
- [ ] Loading + error states for all async operations
- [ ] Git: commit frequently, meaningful messages

### Environments
```bash
development  → local machine
staging      → preview URL (client reviews here)
production   → live site
```

### No Placeholder Policy
Never ship with: placeholder images, fake testimonials, hardcoded API keys,
TODO/FIXME in production, console.log statements, commented-out old code.

### Phase 3 XML Task Spec Pattern
```xml
<plan phase="3">
  <task id="3-01" type="parallel">
    <n>Build homepage and navigation</n>
    <files>src/app/page.tsx, src/components/Nav.tsx, src/components/Footer.tsx</files>
    <depends>none</depends>
    <action>Build homepage matching approved mockup. Nav: desktop + mobile hamburger.
            Footer: identical across all pages. All links wired to correct routes.
            No placeholder content — use actual copy provided by client.</action>
    <verify>Homepage loads at localhost:3000. Nav links work. Mobile menu opens/closes.
            Footer identical on all pages.</verify>
    <done>Homepage renders with real content. Nav + footer fully functional on all devices.</done>
  </task>
  <task id="3-02" type="parallel">
    <n>Build contact form with server validation and email</n>
    <files>src/app/api/contact/route.ts, src/components/ContactForm.tsx</files>
    <depends>none</depends>
    <action>Zod schema validation server-side. Resend SDK for email.
            Return 400 + field errors on invalid. Return 200 on success.
            Rate limit: 5 requests per minute per IP.</action>
    <verify>Invalid submission → 400 + errors shown. Valid → email received.</verify>
    <done>Form validates server-side, sends email, handles errors gracefully.</done>
  </task>
  <task id="3-03" type="sub-agent">
    <n>Generate redirect map from old site</n>
    <action>Crawl old site, map every URL to new equivalent.
            Output spreadsheet: Old URL | New URL | HTTP Status</action>
    <verify>All old URLs accounted for. No 404s on old URL paths.</verify>
    <done>Redirect map complete at .planning/phases/3-redirects.csv</done>
  </task>
</plan>

Wave 1 (parallel): 3-01, 3-02, 3-03
Wave 2: 3-04 (needs 3-01 and 3-02)
```

---

## PHASE 4 — Polish & Consistency Enforcement

**Goal:** Professional on every device, every browser, zero visual inconsistencies.

Read `references/consistency.md` for full CSS token system and element audit.

### Consistency Enforcement — Run First
- [ ] CSS variables / design tokens defined: colours, font sizes, spacing, radius, shadows, z-index.
      Every value from a variable — no magic numbers anywhere.
- [ ] Typography consistent across all pages: H1–H6 styles, body, caption, labels
- [ ] Buttons: single system (primary, secondary, ghost, disabled states)
- [ ] Forms: inputs, labels, placeholders, errors, focus states — all identical
- [ ] Cards: consistent padding, radius, shadow system
- [ ] Icons: single source, consistent size and weight
- [ ] Colours: brand palette only — no rogue hex values
- [ ] Spacing: scale-based (4/8/12/16/24/32/48/64px) — no random margins
- [ ] Navigation: identical across all pages including mobile
- [ ] Footer: identical across all pages
- [ ] Links: consistent colour, underline, hover, active, visited states
- [ ] Image aspect ratios consistent per use context

### Browser & Device Testing
- [ ] Chrome, Firefox, Safari, Edge
- [ ] iOS Safari, Android Chrome, tablet (768px)
- [ ] Test at: 375px, 768px, 1024px, 1280px, 1440px

### Lighthouse Targets
Performance: 90+ | Accessibility: 90+ | Best Practices: 90+ | SEO: 90+

### Final Code Cleanup
- [ ] Remove all `console.log` statements
- [ ] Remove commented-out code
- [ ] Remove unused dependencies (`npm prune`)
- [ ] Remove dead CSS (PurgeCSS or manual)
- [ ] All TODO / FIXME resolved

---

## PHASE 5 — Security & Legal Compliance

**Goal:** Hardened against attacks. Legally compliant. Before going live.

Read `references/security.md` for full header configs, audit commands, OWASP checklist.
Read `references/legal.md` for GDPR, CCPA, India DPDP Act, WCAG legal requirements.

### Security Checklist
- [ ] HTTPS enforced, SSL valid and auto-renewing
- [ ] HTTP → HTTPS redirect configured
- [ ] Security headers set — see `references/security.md`:
      `Strict-Transport-Security`, `Content-Security-Policy`, `X-Frame-Options`,
      `X-Content-Type-Options`, `Referrer-Policy`, `Permissions-Policy`
- [ ] All env vars in host secrets vault — never in source code
- [ ] `npm audit --audit-level=high` clean
- [ ] No sensitive data in Git history
- [ ] Input sanitisation on all forms — server-side
- [ ] Rate limiting on auth endpoints and contact forms
- [ ] CORS: no wildcard `*` on sensitive routes
- [ ] Admin / CMS: strong password + 2FA enforced
- [ ] Database: no direct public access, parameterised queries only
- [ ] File uploads: type validation, size limits, virus scanning
- [ ] Run Mozilla Observatory: observatory.mozilla.org — target A+
- [ ] Run SSL Labs: ssllabs.com/ssltest — target A+
- [ ] OWASP Top 10 review — see `references/security.md`

### Legal Compliance Checklist
- [ ] Privacy Policy — present, linked in footer
- [ ] Terms of Service — present if selling or user accounts exist
- [ ] Cookie consent banner — required if any tracking + EU/UK traffic
- [ ] GDPR compliance if EU users
- [ ] CCPA compliance if California users (revenue threshold applies)
- [ ] WCAG AA accessibility — legal requirement in EU, UK, US, Australia
- [ ] Refund / cancellation policy if e-commerce
- [ ] GST number displayed if India e-commerce

---

## PHASE 6 — QA & Final Review

**Goal:** Every feature works, every link resolves, client signs off in writing.

### QA Checklist
- [ ] Every page loads without console errors
- [ ] Every internal link works (Screaming Frog free or linkchecker)
- [ ] Every form submits and saves/sends correctly
- [ ] Payment flow tested end-to-end with test cards
- [ ] Email notifications received
- [ ] 404 page works for bad URLs
- [ ] CMS: client can log in, create, edit, publish
- [ ] Analytics: events firing in GA4 DebugView
- [ ] Cookie consent: banner shows, preferences saved, analytics respects opt-out
- [ ] All legal pages present and linked
- [ ] Spell check all visible copy
- [ ] Test with slow 3G throttling (Chrome DevTools → Network)
- [ ] Accessibility: axe DevTools or WAVE on all key pages
- [ ] Send staging URL to client for **written sign-off**

QA sign-off template: `references/templates.md` → QA Sign-off Template.
Client must confirm in writing before production deploy.

---

## PHASE 7 — Hosting Setup

**Goal:** Infrastructure provisioned, configured, ready for the site.

Read `references/deployment.md` for platform-specific recipes.

### Hosting Decision Guide

| Need | Recommended |
|------|------------|
| Marketing / landing page | Netlify (free tier) |
| Next.js / SaaS app | Vercel (best Next.js support) |
| Portfolio / blog | Vercel or Netlify |
| E-commerce | Vercel + Stripe, or Shopify |
| WordPress | Kinsta, WP Engine, or Hostinger |
| Full VPS control | DigitalOcean Droplet, Hetzner |
| High-traffic | AWS EC2 + CloudFront, or GCP |

### Hosting Setup Checklist
- [ ] Account under **client's name/email**
- [ ] Domain purchased / transferred
- [ ] DNS: A record, CNAME, MX for email
- [ ] SSL provisioned and auto-renewing
- [ ] Env vars in hosting secrets vault
- [ ] Database provisioned (PlanetScale, Supabase, or RDS)
- [ ] Email service configured if needed
- [ ] Backups enabled (daily minimum)
- [ ] Staging / preview environment set up and tested

---

## PHASE 8 — Deployment & Tracking Setup

**Goal:** Site live. Full tracking wired. Baseline captured. Rollback plan ready.

Read `references/deployment.md` for platform-specific commands.
Read `references/results.md` for GA4 event code and baseline report template.

### Pre-Deploy Checklist
- [ ] All changes merged to main
- [ ] Production env vars verified
- [ ] Database migrations ready
- [ ] Staging build successful
- [ ] Client QA sign-off received (Phase 6)
- [ ] Redirect map ready to verify

### Deployment Checklist
- [ ] Deploy to production
- [ ] Verify site loads at domain (clear cache, incognito)
- [ ] Verify SSL padlock
- [ ] Verify www and non-www resolve
- [ ] Test all critical paths on production
- [ ] **Verify all redirects firing** — crawl old URLs, confirm 301s land
- [ ] **Check crawl budget** — no `noindex` on pages that should rank
- [ ] Set up uptime monitoring (UptimeRobot or Better Stack — free)
- [ ] Document deploy process in README

### Tracking Setup — Non-Negotiable
Without this, Phase 9b is impossible. The baseline report is your proof of results.
- [ ] **GA4**: custom events — form submits, button clicks, phone clicks, scroll depth 75%, purchases
- [ ] **Google Search Console**: property verified, sitemap submitted, coverage checked
- [ ] **Heatmap**: Hotjar or Microsoft Clarity (free) on key pages
- [ ] **Conversion tracking**: all goals tested in GA4 DebugView
- [ ] **Call tracking**: CallRail if client gets inbound calls
- [ ] **Baseline report saved** to `.planning/baseline-[date].md`:
      date, organic impressions, clicks, top keywords, Core Web Vitals, conversion rate

### Rollback Plan
- Vercel / Netlify: one-click rollback in dashboard
- VPS: keep previous release folder, symlink swap
- Docker: `docker pull [previous-tag]`

---

## PHASE 9 — Scalability

**Goal:** Site handles growth without going down or slowing.

### Performance & Scalability Checklist
- [ ] CDN for static assets (Cloudflare free tier or host CDN)
- [ ] Image optimisation: Next/Image, imgproxy, or Cloudinary
- [ ] Caching: static pages (long headers + ISR), API (Redis / edge), DB (PgBouncer)
- [ ] Load test conducted — see commands below
- [ ] Database indexed on frequently queried columns
- [ ] Error monitoring: Sentry (free tier)
- [ ] Performance monitoring: Vercel Analytics / Datadog / New Relic
- [ ] Autoscaling configured (AWS / GCP / Railway)
- [ ] Alert: notify if uptime drops or error rate spikes

### Load Testing
```bash
# k6
k6 run --vus 50 --duration 30s script.js

# Apache Bench
ab -n 1000 -c 50 https://yoursite.com/

# Target: <2s response time under 50 concurrent users
```

### Scalability Tiers
```
<10k/mo:    Free Vercel/Netlify or shared hosting
10k–100k:   Vercel Pro / Netlify Pro / small VPS (2GB)
100k–1M:    Dedicated VPS + CDN + DB read replica
1M+:        Kubernetes / ECS / multi-region
```

---

## PHASE 9b — Post-Launch Results Loop

**Goal:** Prove ROI. Retain the client. Turn results into upsells.

> This is where most freelancers disappear. Don't.
> The results loop turns a one-time project into an ongoing relationship.

Read `references/results.md` for GA4 event setup, report template, CRO experiment log.

### Monthly Reporting Checklist
- [ ] Organic traffic vs. previous period AND vs. launch baseline (the "before")
- [ ] Keyword positions (Search Console → Performance → Queries)
- [ ] Conversion rate per key landing page — surface underperformers
- [ ] Heatmap review: are users clicking CTAs? Where are they dropping off?
- [ ] Core Web Vitals — flag regressions
- [ ] Goal completions in GA4: leads, calls, form fills, purchases
- [ ] Plain-language client summary: "Here's what improved. Here's what we're testing next."

### CRO Cadence — Minimum 1 Experiment Per Quarter
- A/B test: headline copy, CTA text/colour, hero image, form length
- Tools: VWO free / simple manual split, compare in GA4
- Log: hypothesis → change → result → decision
- Show client — justifies the retainer

### Ranking & SEO Monitoring
- [ ] Rank tracking for 10–20 keywords (Search Console, Semrush free, Mangools)
- [ ] Monitor drops — investigate: algorithm update? competitor content? technical issue?
- [ ] Content gap opportunities monthly
- [ ] New backlink opportunities monthly

### Results-to-Retainer
- Traffic up 40% → "let's run Google Ads to amplify it"
- Form at 2% conversion → "industry average is 4% — let's A/B test the CTA"
- Ranking page 2 → "one content piece and two backlinks puts this on page 1"

---

## PHASE 10 — Client Handoff & Ownership Transfer

**Goal:** Client has full control. You've been paid. Liability transferred cleanly.

Read `references/templates.md` for handoff email template.
Read `references/legal.md` for final legal confirmation steps.

### Payment & Legal
- [ ] Final invoice sent
- [ ] **Payment received before transferring anything**
- [ ] Contract end clause confirmed
- [ ] 30-day warranty documented
- [ ] Written handoff sign-off received

### Credentials Transfer
Via 1Password, Bitwarden Send, or encrypted email — never plain email:
- [ ] Hosting account / ownership transfer
- [ ] Domain registrar + registrar lock disabled
- [ ] DNS zone file exported
- [ ] CMS admin credentials
- [ ] Database credentials / connection string
- [ ] Email service account
- [ ] GA4 property ownership → client Google account
- [ ] Stripe → add client as owner
- [ ] Git repo access
- [ ] All production API keys
- [ ] 2FA backup codes or help client set up their own

**After transfer: revoke your own access from every platform.**

### Documentation Package (ZIP or shared folder)
- [ ] `README.md` — how to run/deploy locally
- [ ] `CONTENT.md` — CMS editing guide with screenshots
- [ ] `HOSTING.md` — account details, domain/SSL renewal
- [ ] `MAINTENANCE.md` — how to update dependencies, run backups
- [ ] `CONTACTS.md` — support contacts for each service
- [ ] Design files (Figma link or exported)
- [ ] Brand assets (logo SVGs, fonts, hex codes)

### Handoff Sign-off
Written confirmation (email is fine) that client:
1. Has received all credentials
2. Can access all platforms
3. Accepts site as delivered per original brief
4. Acknowledges warranty terms

---

## COMMON ISSUES & QUICK FIXES

| Problem | Quick Fix |
|---------|----------|
| Site slow on first load | Enable CDN, compress images, add cache headers |
| SSL not working | Check DNS propagation (dnschecker.org), reissue cert |
| Form not sending | Check SMTP credentials, test with Mailtrap first |
| Client locked out of CMS | Reset password via DB or hosting panel |
| Deployment failing | Check env vars on production, check build logs |
| Domain not resolving | DNS TTL delay — wait up to 48h, verify A records |
| Security header missing | Add via `next.config.js`, `.htaccess`, or nginx config |
| Rankings dropped after launch | Check redirects, robots.txt, noindex tags |
| GA4 not receiving data | Check measurement ID, check consent blocking scripts |
| CLS score bad | Images missing width/height — add `aspect-ratio` CSS |

---

## RECURRING REVENUE — POST-HANDOFF UPSELLS

Frame every upsell around results already proven:

- **Maintenance retainer** (₹5k–₹25k/mo / $100–$500/mo): updates, backups, monitoring
- **SEO retainer**: content, link building, rank tracking — sell with keyword gap evidence from Phase 1
- **CRO retainer**: monthly A/B tests — sell with current vs benchmark conversion rate
- **Google Ads / Meta Ads**: logical once organic traffic is established
- **Feature additions**: new pages, integrations, redesigns
- **Hosting management**: you manage it so they don't have to

**Pitch framing:** *"The site is live and performing. Here's what 30 days of data shows.
Here's what's still on the table if we keep improving it together."*

---

*Read the command files in `commands/wsa/` for the full agentic execution protocol.*
*Read the reference files in `references/` when indicated — never proceed on assumptions.*
