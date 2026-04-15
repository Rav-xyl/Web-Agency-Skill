# /wsa:next — Auto-Detect and Run Next Step

Reads STATE.md and ROADMAP.md. Detects what comes next. Confirms with user.

```
Read STATE.md current phase + status

No CONTEXT.md for current phase → /wsa:discuss [phase]
CONTEXT.md exists, no PLAN.md → /wsa:plan [phase]
PLAN.md exists, no SUMMARY.md → /wsa:execute [phase]
SUMMARY.md exists, no UAT.md → /wsa:verify [phase]
UAT has fix queue → /wsa:execute [phase] (run fixes)
UAT all passed → mark phase ✅ in ROADMAP.md → advance → /wsa:next
All phases ✅ → /wsa:handoff
```

Always confirm: "Next step is [X]. Proceed?"
