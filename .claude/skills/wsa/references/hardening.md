# WSA Hardening — Professional Integrity Gate

This module defines the **Senior Partner Standards** for the Web Agency Skill. Any work that fails these checks is considered "Junior Slop" and must be refactored before proceeding to the next phase.

---

## 1. The Placeholder Ban (Zero-Tolerance)
Placeholders are the primary indicator of context decay. They are strictly prohibited in Phase 3+ (Build).

### Automated Integrity Audit
The `/wsa:verify` command executes the following surgical scans. Any match results in an immediate **Gate Failure**.

```powershell
# Placeholder Scan (Run from project root)
# Searches for TODOs, Lorem, console logs, and hardcoded 'adjust later' flags
grep -rE "(TODO:|FIXME:|HACK:|Lorem ipsum|// Implement this later|console\.log\(|height: [0-9]+px; /\* Adjust later \*/)" . --exclude-dir={node_modules,.git,.next,dist}
```

---

## 2. Structural Integrity Gates (Phase 3a)

### [Gate 1] Technical Spec Lock
Before writing code, a `TECHNICAL_SPEC.md` must be created and locked (Integrity Score: +20).

#### [Template] TECHNICAL_SPEC.md
```markdown
# Technical Specification: [Project Name]

## 1. Database Architecture (3NF)
[Mermaid ERD Diagram Here]
- **Normalization Strategy**: [How you handled denormalization for performance]
- **Key Constraints**: [List of FKs and Unique constraints]

## 2. API Schema Registry (Zod)
- **Contracts**: [Link to /src/lib/schemas/ or equivalent]
- **Validation Philosophy**: [Standardized error response format]

## 3. Provider Stack (Discovery Pass)
- **Primary Payment**: [Provider Name] — Verified for [Country]
- **Primary Auth**: [Provider Name]
- **Primary Storage**: [Provider Name]
```

---

## 3. High-Aura CSS Standards (Phase 3b)
- **Token Discipline**: No magic numbers. Colors and spacing must come from the defined design system.
- **Motion GSD**: Every interactive element (Button, Link, Card) must have an defined `hover` and `active` state using the curves defined in `aura.md`.

---

## 4. The Integrity Score (Audit Logic)
Every project state must track an **Integrity Score (0-100)** in `STATE.md`.

| Violation | Penalty |
| :--- | :--- |
| Placeholder found in tracked file | -10 per instance |
| Missing `TECHNICAL_SPEC.md` in Phase 3+ | -30 |
| Non-normalized database schema | -20 |
| Missing Zod validation on public API route | -20 |
| Lighthouse Performance < 90 | -15 |

| Achievement | Bonus |
| :--- | :--- |
| 100% Type Safety (Zero `any`) | +10 |
| Documented ADR (Architectural Decision Record) | +5 |
| E2E tests for core flows | +10 |
```
