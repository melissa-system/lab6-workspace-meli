# Team Workspace Template

A ready-to-clone workspace structure that makes AI agents (GitHub Copilot, Claude Code, Cursor, etc.) effective team members through **progressive disclosure** and **persistent context**.

## Quick Start

```bash
cd my-team-workspace
code Workspace.code-workspace
```

This copy stays local. There is no remote yet.

Then:
1. Edit `AGENTS.md` with your team's specifics
2. Add domain knowledge to `Knowledge/`
3. Configure MCP servers in `.vscode/mcp.json`
4. Set team conventions in `.github/copilot-instructions.md`
5. Start working — the workspace grows as you use it

## What This Gives You

| Feature | How It Works |
|---------|-------------|
| **Progressive disclosure** | AGENTS.md in every directory — agents read only what they need |
| **Persistent knowledge** | Knowledge/ survives across sessions and team members |
| **Reusable playbooks** | Skills/ teaches agents repeatable procedures |
| **Team-wide AI behavior** | copilot-instructions.md sets shared conventions |
| **External tool access** | MCP servers let agents use the tools you connect |
| **Personal + shared** | .gitignore separates private (Machine/, temp/) from shared |

## Structure

```
├── AGENTS.md                         ← Start here (root navigation)
├── .github/copilot-instructions.md   ← Global AI behavior rules
├── .vscode/mcp.json                  ← External tool connections
├── Knowledge/                        ← Durable team knowledge
│   ├── AGENTS.md
│   └── {YourName}-Brain/             ← Personal knowledge base
│       └── daily-log/                ← Session logs
├── Skills/                           ← Reusable playbooks
│   └── AGENTS.md
├── Repos/                            ← Repo index (.gitignored)
│   └── AGENTS.md
├── Machine/                          ← Local config (.gitignored)
│   └── AGENTS.md
└── temp/                             ← Scratch space (.gitignored)
    └── AGENTS.md
```

## Design Principles

1. **Every directory has an AGENTS.md** — the agent's signpost
2. **TL;DR first** — one-line summary at the top of every AGENTS.md
3. **Shared via Git, private via .gitignore** — team context is versioned; personal files stay local
4. **Knowledge compounds** — findings documented today help every future session
5. **Skills are reusable** — document a procedure once, agent executes it forever

## License

MIT License. See [LICENSE](LICENSE).
