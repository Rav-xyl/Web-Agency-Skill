# Web Agency Skill (WSA) — The Full-Stack Pro Framework

A senior-level, spec-driven, and agent-agnostic operating system designed for solo developers and agency partners to orchestrate high-fidelity web projects with absolute precision.

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Aura: High](https://img.shields.io/badge/Aura-High-blueviolet)
![PRs: Welcome](https://img.shields.io/badge/PRs-Welcome-brightgreen)

---

## ⚡ Quickstart (30 Seconds)

1. **Clone**: `git clone https://github.com/Rav-xyl/Web-Agency-Skill`
2. **Ingest**: Point your AI assistant (Claude, Cursor, Windsurf) to the repo root.
3. **Initialize**: Type `/wsa:init` to bootstrap your professional project lifecycle.

---

## 🎭 The Mindset: Senior Full-Stack Partner
Unlike generic prompts, **WSA** codifies the standards of a senior professional. It mandates normalized database schemas, hardened API contracts, and high-aura cinematic UI/UX. It operates with a **Zero Placeholder Tolerance** policy—if it's in the repo, it's production-ready.

---

## 🏛️ GSD Architecture (Lifecycle)

The WSA operating system follows a strict, spec-driven lifecycle to ensure **Architectural Integrity** and prevent **Context Rot**.

![WSA Launch Visual](Launch_Visual.png)

```mermaid
graph TD
    subgraph PROSPECT["🎯 STRATEGIC ENTRY"]
        P0["Phase 0: Cold Pitch & Qualification"]
    end

    subgraph PLAN["📐 SYSTEM DESIGN"]
        P1["Phase 1: Discovery & Scoping"]
        P2["Phase 2: Dynamic Design System"]
    end

    subgraph BUILD["⚡ FULL-STACK IMPLEMENTATION"]
        P3A["Phase 3a: Hardened Backend"]
        P3B["Phase 3b: High-Aura Frontend"]
    end

    subgraph HARDEN["🛡️ QUALITY ASSURANCE"]
        P4["Phase 4: Pixel-Perfect QA"]
        P5["Phase 5: Security & Compliance"]
    end

    subgraph SHIP["🚀 PRODUCTION SHIP"]
        P8["Phase 8: Deployment & Tracking"]
    end

    subgraph GROW["📈 RESULTS LOOP"]
        P9["Phase 9: Performance Optimization"]
        P9B["Phase 9b: Monthly Growth Loop"]
    end

    P0 --> P1 --> P2
    P2 --> P3A --> P3B
    P3B --> P4 --> P5
    P5 --> P8 --> P9 --> P9B
    P9B -.->|"Retainer Feedback"| P1

    %% Persistent State Layer
    STATE[("📂 PERSISTENT CONTEXT<br/>(STATE.md / PROJECT.md)")]
    STATE -.-> |"Guardrail Injection"| P3A
    STATE -.-> |"Guardrail Injection"| P3B
    STATE -.-> |"Decision Tracking"| P9B

    %% Styles
    classDef senior fill:#000,stroke:#6c63ff,stroke-width:2px,color:#fff;
    classDef process fill:#1a1a1a,stroke:#333,stroke-width:1px,color:#ccc;
    classDef logic fill:#0a0a1a,stroke:#ff6b6b,stroke-width:2px,color:#fff;

    class P0,P8,P9B senior;
    class P1,P2,P4,P5,P9 process;
    class P3A,P3B logic;
```

---

## 📂 Repository Blueprint

```text
.
├── .claude/
│   └── skills/
│       └── wsa/
│           ├── assets/       # State schemas & operational assets
│           ├── commands/     # Precision action logic (/wsa:init, /wsa:plan)
│           ├── references/   # Hardened knowledge (Security, Aura, Backend)
│           └── SKILL.md      # The Brain (Central orchestrator)
├── .cursor/
│   └── rules/                # Native IDE guardrails (.mdc)
├── AGENTS.md                 # Global operational standards
├── CLAUDE.md                 # Model-specific expert overrides
└── README.md                 # Senior Partner Manifesto
```

---

## 🛠️ Operational Router

Point your AI assistant to this root and trigger the skill:
> "Ingest the Web Agency Skill. Read AGENTS.md and initialize Phase 1."

| Command | Action |
| :--- | :--- |
| `/wsa:init` | Bootstrap a fresh professional project. |
| `/wsa:audit` | Ingest legacy code and create a recovery roadmap. |
| `/wsa:plan [N]` | Generate atomic XML task specs for Phase N. |
| `/wsa:execute` | Run surgical, one-task-per-commit development waves. |
| `/wsa:verify` | Execute the pro-level QA and fix queue. |

---

## 🛡️ Pro Modules Included
- **[High-Aura UI/UX](./.claude/skills/wsa/references/aura.md)**: Cinematic motion and visual depth standards.
- **[Backend Integrity](./.claude/skills/wsa/references/backend.md)**: DB normalization and API hardening patterns.
- **[Security & legal](./.claude/skills/wsa/references/security.md)**: OWASP standards and GDPR compliance.

---

## 🚫 What This Is NOT
- **It is NOT a CLI tool**: It is a collection of logic and references that your AI assistant uses to guide its own CLI usage.
- **It is NOT a SaaS**: It's an open-source framework for building high-end client projects.
- **It is NOT a "Prompt"**: It's a structured operating system with state management and automated gates.

---

## 📄 License
Licensed under the **MIT License**. Build something legendary.
