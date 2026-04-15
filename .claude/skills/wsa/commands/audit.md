# /wsa:audit — Existing Project Audit

For inherited sites, existing codebases, or "take over this project" requests.
Do NOT write any code until the audit report is complete and confirmed by user.
Creates: PROJECT.md, STATE.md, AUDIT-REPORT.md

---

## Step 1 — Ingest & Understand

Read everything before touching anything:
- All entry points (index.html, app/page.tsx, etc.)
- All CSS/SCSS/Tailwind config files
- package.json — framework, dependencies, versions
- .env.example or config files — all integrations
- Existing README or docs if present

Identify:
- Framework, build tool, CMS
- Third-party scripts (analytics, chat, payments)
- Current analytics setup (GA4? nothing?)
- Business type from content
- Target audience from copy, CTAs, page structure
- Every page / route
- What is unfinished, broken, or missing

---

## Step 2 — Score the Project

Apply Phase 0.5 scoring matrix from ../SKILL.md.
Score determines how deep to go on each fix phase.

---

## Step 3 — Run Consistency Audit

Read `../references/consistency.md` for the full CSS token and element system.

For large codebases (Score 12+), dispatch parallel sub-agents:
- Sub-agent A: CSS + element consistency audit
- Sub-agent B: Security + headers audit
- Sub-agent C: SEO + meta + schema audit
- Sub-agent D: Performance + Lighthouse audit

See `../references/sub-agents.md` for dispatch template.

For smaller projects, run all checks in current context.

**CSS audit:** tokens defined? hardcoded values? dead CSS? inconsistent breakpoints?
**Element audit:** buttons, typography, forms, cards, links, icons, spacing, colours, nav, footer, 404
**Code audit:** copy-pasted HTML? console.logs? committed secrets? TODO in prod? messy structure?
**Functionality audit:** pages load? links resolve? forms work? analytics firing? meta tags? schema?
**Security audit:** HTTPS? security headers? env vars safe? dependencies audited?

---

## Step 4 — Write AUDIT-REPORT.md

Before touching any code:

```markdown
## Existing Project Audit Report
Date: [date]

### Business Profile
Type: [e.g. local bakery, SaaS, portfolio]
Audience: [inferred]
Stack: [framework, CMS, hosting]
Complexity score: [X/20]
Pages/routes: [list]

### Findings — CSS Consistency
| Issue | Location | Severity | Fix |
|-------|----------|----------|-----|

### Findings — Element Consistency
| Issue | Location | Severity | Fix |
|-------|----------|----------|-----|

### Findings — Code Quality
| Issue | Location | Severity | Fix |
|-------|----------|----------|-----|

### Findings — Functionality & SEO
| Issue | Location | Severity | Fix |
|-------|----------|----------|-----|

### Findings — Security
| Issue | Severity | Fix |
|-------|----------|-----|

### Missing Tracking
- GA4: [present/missing/misconfigured]
- Search Console: [present/missing]
- Heatmap: [present/missing]

### Priority Fix Order
1. Critical security (exposed keys, missing HTTPS)
2. Broken functionality (forms, links, critical paths)
3. Consistency cleanup (CSS tokens, element system)
4. Missing tracking (GA4, Search Console)
5. SEO gaps (meta, schema, sitemap)
6. Polish and visual consistency
```

---

## Step 5 — Create State Files

After user confirms the report, create PROJECT.md and STATE.md.
Set current phase in STATE.md based on the site's actual state:
- Functional but inconsistent → Phase 4
- Functional but insecure → Phase 5
- Functional and consistent but not live → Phase 6
- Live but missing tracking → Phase 8

Confirm correct entry point with user before proceeding.

---

## Step 6 — Fix in Priority Order

Only after user approves the fix order.
Every fix must be an XML task spec — see ../SKILL.md Operating System section.
One commit per fix. Never batch.
Never create placeholder content.
