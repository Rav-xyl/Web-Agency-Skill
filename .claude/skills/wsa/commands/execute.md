# /wsa:execute N — Run All Tasks in Phase N

Executes all tasks from N-PLAN.md in wave order. Commits after each task.
Reads: .planning/phases/N-PLAN.md, PROJECT.md, STATE.md
Creates: .planning/phases/N-SUMMARY.md, git commits

---

## Before Starting

1. Confirm N-PLAN.md exists. If not → run `/wsa:plan N` first.
2. Read PROJECT.md and STATE.md for full context.
3. Read the entire plan file before starting any task.
4. Check all dependencies from prior phases are complete in STATE.md.

---

## Per-Task Protocol

1. Read the spec completely — action, verify, done
2. Execute the action exactly — no shortcuts, no scope additions
3. Run the verify check — if it fails, fix before proceeding
4. Confirm done criteria are observably true
5. **Commit immediately** using surgical staging:

```bash
git add [only files changed in this specific task]
git commit -m "feat(phase-N): [id] — [task name]"
# e.g. feat(phase-3a): 3a-01 — implement hardened auth middleware
```

**CRITICAL: Never batch multiple tasks into one commit. Never use `git add .` unless the task created a new directory structure.**

For `type="sub-agent"` tasks:
- Read `../references/sub-agents.md` for dispatch template
- Provide: full context block, exact task spec, output format, constraints
- Wait for return, validate format, integrate results, update STATE.md

---

## What NOT To Do

- Never skip a verify step
- Never create placeholder content
- Never commit `console.log`, TODO, commented-out code, or secrets
- Never change scope mid-execution — add to STATE.md open items instead

---

## After All Waves Complete

1. Update STATE.md: advance phase, record last action, resolve open items
2. Update ROADMAP.md: mark phase N as ✅ Complete
3. Write .planning/phases/N-SUMMARY.md:

```markdown
## Phase N Summary
Completed: [date]
Tasks: [list of IDs and names]
Files changed: [list]
Commits: [list of hashes]
Verify results: [pass/fail per task]
Issues during execution: [list or "none"]
Next: Phase [N+1]
```

4. Run `/wsa:verify N`.
