# /wsa:discuss N — Capture Phase Decisions

Captures implementation preferences before planning phase N.
Reads: PROJECT.md, STATE.md, ROADMAP.md
Creates: .planning/phases/N-CONTEXT.md

---

The roadmap has a line or two per phase. That is not enough context to build things
the way you imagine them. This step locks in decisions before planning runs.

Read the phase description from ../SKILL.md. Identify gray areas for what's being built.
Ask targeted questions — not all at once. Ask until intent is clear.

**Gray areas by phase type:**

Phase 2 (Design): visual direction, layout density, CTA style, trust signals priority,
mobile-specific behaviour, animation philosophy

Phase 3 (Build): which components must be reusable, form validation UX, image handling,
navigation behaviour, performance priorities per page

Phase 4 (Polish): existing tokens to preserve or clean slate, motion philosophy,
font loading strategy, dark mode requirement

Phase 5 (Security): user auth present? payments? EU/UK users? India e-commerce?

Phase 8 (Deploy & Track): call tracking needed? GA4 fresh or existing property?
purchase tracking? any existing analytics to migrate?

**Output format — .planning/phases/N-CONTEXT.md:**
```markdown
## Phase N Context — [Phase Name]
Captured: [date]

### Visual / UX decisions
- [Decision: preference + reason]

### Technical decisions
- [Decision: what + why]

### Locked decisions (do not change without flagging)
- [e.g. "No dark mode — client explicitly declined"]

### Open questions (research targets for /wsa:plan N)
- [What still needs investigation]
```

Planner reads this file. Locked decisions are locked. Open questions become research targets.
