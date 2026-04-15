# /wsa:plan N — Research + Create Task Specs

Research phase N, then create XML task specs ready for execution.
Reads: PROJECT.md, STATE.md, REQUIREMENTS.md, .planning/phases/N-CONTEXT.md
Creates: .planning/phases/N-RESEARCH.md, .planning/phases/N-PLAN.md

---

## Step 1 — Research

Dispatch research sub-agent to investigate:
- How to implement this phase with the decided stack
- Open questions from N-CONTEXT.md
- Libraries, patterns, or pitfalls for what's being built
- Phase-specific reference material:

| Phase | Research targets |
|-------|-----------------|
| 2 | High-aura layouts & cinematic motion patterns (Refer: `references/aura.md`) |
| 3a | Professional DB modeling, API Hardening & Auth logic (Refer: `references/backend.md`) |
| 3b | Modular component architecture, zero-placeholder asset pipeline |
| 4 | CSS Token systems, visual depth, and typography pairings |
| 5 | Security headers, OWASP hardening, and legal compliance (Refer: `references/security.md`) |
| 6 | Technical QA, browser testing, and a11y audit |
| 8 | GA4 event tracking and results baseline capture (Refer: `references/results.md`) |
| 9 | Load testing and edge-optimized scalability |
| 9b | MRR recurring revenue and CRO experiment logs |

Write findings to .planning/phases/N-RESEARCH.md.

---

## Step 2 — Create XML Task Specs

After research, write atomic task specs. Read current project state from PROJECT.md and STATE.md at root.
See Operating System section of ../SKILL.md for state tracking rules.

Rules:
- 3–6 tasks per phase. Split large phases into N-PLAN-A.md and N-PLAN-B.md if needed.
- Each task small enough to execute in a fresh context window.
- task type: `auto` (sequential), `parallel` (same wave), `sub-agent` (fresh context)
- `<depends>` must reference exact task IDs that must complete first, or "none"
- `<verify>` must be a concrete, runnable check — not "make sure it works"
- `<done>` must be an observable truth — not "task is done"

---

## Step 3 — Group Into Waves

At bottom of plan file:
```
## Execution Waves
Wave 1 (parallel): N-01, N-02
Wave 2 (sequential): N-03 (needs N-01)
Wave 3 (sequential): N-04 (needs N-02 + N-03)
```

---

## Step 4 — Verify Plan Against Requirements

Before finalising:
- Read PROJECT.md and STATE.md. Ensure Phase N is next on ROADMAP.md.
- If Phase 2 (Design), read Phase 1 Discovery results in PROJECT.md.
- If Phase 3 (Build), read Phase 2 Design decisions in STATE.md.
- Refer to the Operating System (GSD) section in ../SKILL.md for the XML spec standard.
- Does this plan deliver every requirement scoped to phase N in REQUIREMENTS.md?
- Does it respect every locked decision in N-CONTEXT.md?
- Could any task regress something from a prior phase?

If gaps → add tasks. If conflicts → flag to user before proceeding.
