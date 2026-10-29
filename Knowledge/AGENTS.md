# Knowledge

> **TL;DR:** Durable reference notes and facts about projects/systems/domains — not step-by-step procedures. Browse subfolders for topic-specific notes.

## What belongs here

- Notes on specific repositories/projects (architecture summaries, conventions, gotchas).
- Domain knowledge that informs decisions (e.g. company terminology, system diagrams, API references).
- Decisions and their rationale that should persist across sessions.
- Personal knowledge bases in `{YourName}-Brain/` subfolders.

## What does NOT belong here

- Reusable step-by-step procedures — put those in [../Skills/AGENTS.md](../Skills/AGENTS.md).
- Transient working files — put those in [../temp/AGENTS.md](../temp/AGENTS.md).
- Actual source code — that lives in [../Repos/AGENTS.md](../Repos/AGENTS.md).

## Personal Knowledge Base

Each team member can create a personal subfolder:

```
Knowledge/{YourName}-Brain/
├── daily-log/          ← date-stamped session logs
│   ├── YYYY-MM-DD.md
│   └── status.md      ← rolling snapshot (agent reads this first each day)
├── {topic}.md          ← verified findings, one file per topic
└── AGENTS.md           ← describes your personal KB
```

**Daily log tip:** Have your AI agent write a summary at the end of each session. Next session, it reads `status.md` and picks up where you left off.

## Conventions

- Organize by topic/project in subfolders or individual Markdown files.
- Prefer concise, well-structured notes over long prose so they're cheap to load into context.
- Keep entries up to date — remove or correct stale information rather than letting it accumulate.
