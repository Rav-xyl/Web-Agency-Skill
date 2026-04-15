# Sub-Agent Dispatch Reference

## When to Dispatch

Dispatch a sub-agent when a task is:
- **Independent**: doesn't need the primary agent's current output to proceed
- **Parallelisable**: can run while the primary agent works on something else
- **Context-heavy**: would consume too much of the primary agent's context window
- **Repetitive**: same operation across many files or pages

Never dispatch for tasks that need real-time back-and-forth with the user.

---

## Tasks Suited for Sub-Agent Dispatch

| Task | When to Dispatch | Expected Output Format |
|------|-----------------|----------------------|
| SEO audit | Content is final | Markdown table: Page | Issue | Fix |
| Security audit | Site at staging | Markdown checklist with severity (Critical / High / Medium) |
| Performance / Lighthouse | Deployed to staging | Scores per page + top 3 fixes |
| Competitor research | Phase 1, always parallel | Brief: competitor URL, top keywords, top pages, speed score |
| Redirect map generation | Old site accessible | Spreadsheet: Old URL | New URL | Status code |
| Image optimisation audit | All images known | List: filename | current size | target size | format |
| Content gap analysis | Site live, GSC connected | List: keyword | search volume | current rank | recommended page |
| Monthly results report | Monthly, always independent | Filled report template from results.md |
| Accessibility audit | Before launch | Page-by-page: issue | WCAG criterion | fix |
| CSS consistency audit | Before Phase 4 ends | List: file | line | issue | fix |

---

## Dispatch Template

When sending a task to a sub-agent, always include all five sections.
Incomplete dispatches return incomplete or wrong results.

```
## Sub-Agent Dispatch

**Task:** [exact task name]

**Context:**
- Business: [name, type, e.g. "Bengaluru restaurant, casual dining"]
- URL / Files: [live URL or file paths]
- Stack: [e.g. Next.js 14, Tailwind CSS, Sanity CMS, Vercel]
- Phase we're in: [e.g. Phase 4 — Polish]
- Phase 0.5 score: [X/20]

**Specific Task:**
[Exact instructions — what to do, what to look at, what to produce]

**Constraints — Do NOT:**
- Do not modify any files
- Do not make assumptions about missing content — flag them
- Do not flag issues already documented in: [link or description]

**Output Format:**
[Exact format expected — markdown table, numbered list, filled template, etc.]

**Hand-back Trigger:**
Return results when: [condition — e.g. "audit of all pages complete" or "top 10 issues identified"]
```

---

## Dispatch Examples

### SEO Audit Dispatch
```
## Sub-Agent Dispatch

**Task:** SEO Audit

**Context:**
- Business: Priya's Bakery, local bakery in Bengaluru
- URL: https://priyasbakery.com (staging)
- Stack: Next.js, Vercel
- Phase: 6 (QA)
- Score: 7/20

**Specific Task:**
Audit all 8 pages for:
1. Title tag — present, unique, <60 chars, includes primary keyword?
2. Meta description — present, unique, <160 chars, includes CTA?
3. H1 — present, exactly one per page, matches page topic?
4. Images — all have descriptive alt text?
5. Schema markup — LocalBusiness schema on homepage?
6. Internal links — reasonable internal linking between pages?
7. Page speed — run pagespeed.web.dev for mobile, note LCP and CLS scores

**Constraints:**
- Do not modify any files
- Do not flag styling issues — SEO only

**Output Format:**
Markdown table: Page | Issue Type | Issue Description | Fix | Priority (High/Med/Low)

**Hand-back Trigger:**
All 8 pages audited.
```

### Security Audit Dispatch
```
## Sub-Agent Dispatch

**Task:** Security Audit

**Context:**
- Project: E-commerce site, Next.js + Stripe
- Staging URL: [URL]
- Phase: 5 (Security)

**Specific Task:**
1. Check all security headers using securityheaders.com — list missing headers
2. Run npm audit and list all High + Critical vulnerabilities
3. Check all API routes — are any unprotected that shouldn't be?
4. Check .env.example — are all required variables documented?
5. Check form inputs — is there server-side validation on all endpoints?

**Constraints:**
- Do not modify files
- Do not run penetration tests on production

**Output Format:**
Markdown checklist grouped by severity: Critical | High | Medium | Low
Each item: Issue | Location | Fix

**Hand-back Trigger:**
All 5 checks complete.
```

---

## Context Window Management

### When to Create a Project State Snapshot

Proactively offer a snapshot when:
- Conversation exceeds ~15 back-and-forth turns
- User says they'll continue in a new session
- A major phase is complete and the next phase is starting
- Any time the agent itself feels uncertain about a prior decision

### Project State Snapshot Format

```
## Project State Snapshot
[Save this to continue in a new session]

**Project:** [Business name + type]
**URL:** [live or staging URL]
**Stack:** [full tech stack]
**Phase 0.5 Score:** [X/20]
**Current Phase:** [phase number and name]

**Decisions Made:**
- Stack: [e.g. Next.js 14 + Sanity + Vercel]
- Hosting: [e.g. Vercel Pro, client account]
- CMS: [e.g. Sanity, client can edit pages/blog]
- Analytics: [e.g. GA4 installed, events configured]
- Auth: [e.g. N/A for this project]
- Payments: [e.g. Stripe, test mode verified]

**Completed Phases:** [list]

**Open Items:**
- [ ] [Item 1 with exact next action]
- [ ] [Item 2]

**Known Issues:**
- [Issue 1 — not yet fixed, reason]

**Next Action:**
[Exact next step — what to do first in the new session]

**Reference Files Used:**
- security.md — Phase 5 complete
- consistency.md — Phase 4 in progress
```

---

## Sub-Agent Return Integration

When a sub-agent returns results, the primary agent must:

1. **Validate the output**: is it in the expected format? Is anything missing?
2. **Triage the findings**: sort by priority — Critical first, then High, then Medium
3. **Integrate into the current phase**: add items to the active checklist
4. **Update the Project State Snapshot**: mark the dispatched task as complete
5. **Inform the user**: summarise what the sub-agent found in plain language before diving into fixes

Never silently apply sub-agent findings without telling the user what was found.
