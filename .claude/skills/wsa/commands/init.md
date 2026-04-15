# /wsa:init — New Project Initialization

Runs: Phase 0.5 profiling → Phase 1 discovery → creates all state files.
Creates: PROJECT.md, STATE.md, REQUIREMENTS.md, ROADMAP.md

---

## Step 1 — Run Phase 0.5 Profiling

Ask the three question clusters from ../SKILL.md → Phase 0.5.
Do not ask all at once. Ask conversationally, cluster by cluster.
Do not proceed until all three clusters are answered.

Score the project (4–20). Determine stack. Write the one-paragraph Project Profile.
Get user confirmation before continuing.

---

## Step 2 — Run Phase 1 Discovery

Work through the Client Intake Checklist from ../SKILL.md → Phase 1.
Capture KPIs, results baseline, legal/contract status.
Dispatch competitor SEO research as sub-agent if needed (see ../references/sub-agents.md).

---

## Step 3 — Write State Files

Create all four files using schemas from ../SKILL.md → State File Schemas.

**PROJECT.md** — populated with all profile + discovery data
**REQUIREMENTS.md** — all features scoped per phase, v2 deferrals listed
**ROADMAP.md** — all phases listed, Phase 0.5 and 1 marked ✅ Complete, rest ⬜
**STATE.md** — current phase: 2, status: not started, all decisions documented

---

## Step 4 — Confirm & Proceed

Present summary to user:
> "State files created. Here's the project profile: [summary].
> Ready to move to Phase 2 — Design. Run `/wsa:discuss 2` to start."

Update STATE.md. Done.
