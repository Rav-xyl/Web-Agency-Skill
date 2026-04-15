# WSA Hardening — Professional Integrity Gate

This module defines the **Senior Partner Standards** for the Web Agency Skill. Any work that fails these checks is considered "Junior Slop" and must be refactored before proceeding to the next phase.

---

## 1. The Placeholder Ban (Zero-Tolerance)
Placeholders are the primary indicator of context decay. They are strictly prohibited in Phase 3+ (Build).

**Forbidden Patterns:**
- `TODO:`, `FIXME:`, `HACK:`
- `Lorem ipsum...`
- `// Implement this later`
- `console.log("here")` (in production-ready files)
- `height: 100px; /* Adjust later */`

**Enforcement:**
- The `/wsa:verify` command will fail if any of these patterns are detected in non-test files.
- **Rule**: If a feature isn't ready, it should be in the `ROADMAP.md` (v2), not a placeholder in v1.

## 2. Structural Integrity Gates (Phase 3a)
Before writing a single line of business logic, the **Technical Foundation** must be locked.

### [Gate 1] 3NF Database Enforcement
- No redundant data. Every field must depend on the whole key.
- Mandatory ERD (Mermaid) in `TECHNICAL_SPEC.md`.
- No `SELECT *` in persistence layers.

### [Gate 2] The Zod Registry (Contract-First)
- Every API endpoint and Environment Variable **must** have a Zod schema.
- No "Implicit Types." If data enters the system, it must be validated at the edge.
- **Goal**: Type safety from DB to UI.

## 3. High-Aura CSS Standards (Phase 3b)
"Boring UI" is a business risk.

- **Token Discipline**: No magic numbers. Colors and spacing must come from the defined design system.
- **Motion GSD**: Every interactive element (Button, Link, Card) must have an defined `hover` and `active` state.
- **Layout Hardening**: Test all UI at 320px (Mobile) and 2560px (Ultra-wide).

## 4. Security & Hardening (Phase 5)
- **Headers**: Mandatory OSSP/OWASP headers (CSP, HSTS).
- **Sanitization**: Zero trust for User Generated Content (UGC).
- **Dependency Audit**: `npm audit` must return 0 critical vulnerabilities.

---

## The Integrity Score
Every project state must track an **Integrity Score (0-100)**:
- **-10** for every placeholder found.
- **-20** for missing Zod contracts on public APIs.
- **-30** for non-normalized database schemas.
- **+10** for 80%+ test coverage.
