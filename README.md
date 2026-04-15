# Web Agency Skill (WSA)

A modular, spec-driven, agent-agnostic framework for running a professional web design and development agency using AI assistants.

Inspired by [GitNexus](https://github.com/abhigyanpatwari/GitNexus), this repository provides a full lifecycle workflow from business prospecting and cold-pitching to post-launch scaling and maintenance.

## 🚀 Concept
This is not just a prompt. It is a **Skill**—a codified operating system for AI agents. It uses the **GSD (Get Shit Done) Architecture** to solve context rot and ensure production-grade results.

- **Atomic Phases**: 11 distinct phases of a web project.
- **Spec-Driven**: Every task is defined in XML before execution.
- **State-Oriented**: Project facts are stored on disk (`PROJECT.md`, `STATE.md`), not held in the AI's ephemeral memory.
- **Multi-Agent**: Orchestrates specialized routines for SEO, Security, and Design.

## 📂 Repository Structure
```text
.
├── .claude/
│   └── skills/
│       └── wsa/
│           ├── assets/       # State schemas and visual assets
│           ├── commands/     # Command logic for every phase (/wsa:init, etc.)
│           ├── references/   # deep knowledge (Security, Legal, Pricing, SEO)
│           └── SKILL.md      # Main skill entry point
├── .cursor/
│   └── rules/                # Cursor IDE specific rules (wsa.mdc)
├── AGENTS.md                 # Global agent operation standards
├── CLAUDE.md                 # Claude-specific context overrides
└── README.md
```

## 🛠️ Getting Started
To use this skill, point your AI assistant to the local copy of this repository and say:
> "Ingest the Web Agency Skill and check for an existing project state."

### Key Commands
- `/wsa:init`: Initialize a new project from scratch.
- `/wsa:audit`: Ingest and audit an existing/legacy codebase.
- `/wsa:results`: Generate growth reports for retainer clients.
- `/wsa:next`: Automatically detect the current phase and execute the next task.

## 💼 Business Modules
Included are professional modules for:
- [Value-Based Pricing](./.claude/skills/wsa/references/pricing.md)
- [Monthly Retainers](./.claude/skills/wsa/references/retainer.md)
- [Cold Pitching](./.claude/skills/wsa/references/cold-pitch.md)
- [Legal & GDPR](./.claude/skills/wsa/references/legal.md)

## 📄 License
This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.
