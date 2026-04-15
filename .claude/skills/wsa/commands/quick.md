# /wsa:quick [task] — Ad-Hoc Task

For tasks that don't need full phase planning — a fix, small addition, one-off change.
Creates: .planning/quick/[slug]/PLAN.md, SUMMARY.md

---

1. Understand the task — ask one clarifying question if needed
2. Write the XML task spec (same format as /wsa:plan)
3. Execute — follow execute.md protocol exactly
4. Commit: `fix(quick): [task description]`
5. Write SUMMARY.md — what changed, files, commit hash

**Flags:**
`/wsa:quick [task] --research` → spawn research sub-agent before planning
`/wsa:quick [task] --verify` → run user acceptance test after execution
