# /wsa:verify N — User Acceptance Testing

Walk user through deliverables one at a time. Create fix plans for failures.
Reads: .planning/phases/N-SUMMARY.md, REQUIREMENTS.md
Creates: .planning/phases/N-UAT.md, fix task specs if issues found

---

## Step 1 — Extract Testable Deliverables

From N-SUMMARY.md and REQUIREMENTS.md, list everything the user should now be able to do.
Present one at a time — not as a wall.

## Step 2 — Walk Through Each

For each: describe what to test and how.
Ask: "Does this work as expected? Yes — or describe what's wrong."
If YES → mark passed. If NO → capture exact failure.

## Step 3 — Handle Failures

For each failure: diagnose, write fix task spec in XML format, add to N-UAT.md fix queue.
After all items: "There are [X] fixes. Run `/wsa:execute N` to apply them."

## UAT Report

```markdown
## Phase N — UAT Report
Date: [date]

| Deliverable | Status | Notes |
|-------------|--------|-------|
| [item] | ✅ Pass | |
| [item] | ❌ Fail | [what's wrong] |

## Fix Queue
[XML task specs for each failure]

## Sign-off
All passed: YES / NO
Proceed to Phase [N+1]: YES / pending fixes
```
