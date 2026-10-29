# Workspace

> **TL;DR:** Espacio de trabajo de Melissa Campos para UNA Chat (Paradigmas de Programación, UNA). Al iniciar, lee `brain/daily-log/status.md`; luego baja al `AGENTS.md` de la carpeta relevante. El código está en `Repos/lab5-paradigmas-meli/`.

This is a shared team workspace designed so AI agents (GitHub Copilot, Claude Code, Cursor, etc.) can navigate efficiently using **progressive disclosure** — reading only what they need, when they need it.

## Structure

- [Knowledge/](Knowledge/AGENTS.md) — Durable reference material, notes, and facts about projects, systems, and domains.
- [Skills/](Skills/AGENTS.md) — Reusable, task-specific playbooks the agent can invoke for known classes of work.
- [Repos/](Repos/AGENTS.md) — Index of cloned source code repositories. Actual repos are **not** tracked here (see `.gitignore`); only `Repos/AGENTS.md` is. Current repo: `lab5-paradigmas-meli` (UNA Chat).
- [brain/](brain/INDEX.md) — Memoria persistente (segundo cerebro, vault de Obsidian). Ver sección **Brain** al final de este archivo.
- [Machine/](Machine/AGENTS.md) — This-computer-specific items (startup scripts, local config). **Not** tracked in Git (see `.gitignore`).
- [temp/](temp/AGENTS.md) — Scratch space for transient files, working notes, and intermediate artifacts. Safe to clear at any time.

## How to navigate

Each directory contains its own `AGENTS.md` describing its purpose, conventions, and what to expect inside — read that file before doing deep work in a directory (progressive disclosure). Start here, then descend only into the directory relevant to the current task.

### TL;DR convention

Every `AGENTS.md` starts with a one-line `> **TL;DR:**` blockquote directly under its title. When navigating:

1. Read only the title + TL;DR line first — that's usually enough to decide whether the directory is relevant to the current task.
2. Only read the rest of the file if the TL;DR isn't sufficient (e.g. you need conventions, examples, or the what-belongs/doesn't-belong rules).
3. Do not skip the TL;DR itself — it's the cheapest signal for whether to go deeper.

When adding a new `AGENTS.md`, write its TL;DR last, after the rest of the content is settled, so it accurately compresses the file.

## Proyecto actual

- **Producto:** UNA Chat — chat en tiempo real (Node.js, Express 5, Socket.IO) con validación anti-XSS y soporte de imágenes/videos.
- **Repo:** [Repos/lab5-paradigmas-meli](Repos/AGENTS.md) — OpenSpec dentro del repo (`openspec/`).
- **Tarea en curso:** US-01 autenticación social con Auth0 + despliegue en Vercel (Laboratorio 8). Se trabaja con OpenSpec dentro del repo.

## Getting Started

1. **Clone this repo** to your machine.
2. **Create your personal Knowledge base:** `Knowledge/{YourName}-Brain/` (add it to `.gitignore` if you want it private, or leave it shared).
3. **Link your repos:** Create a junction/symlink at `Repos/` pointing to your local repositories folder, or just use `Repos/AGENTS.md` as an index.
4. **Configure MCP servers:** Edit `.vscode/mcp.json` with the tools this workspace should use.
5. **Add team knowledge:** Document your projects, conventions, and architecture in `Knowledge/`.

## MCP Servers

MCP server configuration lives in [.vscode/mcp.json](.vscode/mcp.json). Add the servers this workspace should use.

## Customization

- **copilot-instructions.md** — Global rules applied to every AI interaction. Edit `.github/copilot-instructions.md` to set team-wide conventions.
- **AGENTS.md in every directory** — Add one to any new folder so agents (and humans) know what it contains.

---

# Brain: an Obsidian second brain your agents keep for you

> **TL;DR for agents:** This workspace has a brain: an Obsidian vault of short, linked notes at `brain/` (create it if it's missing; see "First run"). At the start of every session, read `brain/daily-log/status.md` and today's diary. During the session, log real work to today's diary as it happens. Before you finish, put any durable finding in the right note and refresh `status.md`. Never store secrets in the brain.

## For the person setting this up

1. Save this file as `AGENTS.md` in your workspace root (the folder you open in your editor or agent). If an `AGENTS.md` is already there, paste this whole file at the end of it instead.
2. OpenCode CLI: run `opencode` in that same root. It loads `AGENTS.md` from there. It does not read `CLAUDE.md` or `@AGENTS.md`. To load this file under its current name instead of merging it into `AGENTS.md`, add `opencode.json` in the root:

   ```json
   {
     "$schema": "https://opencode.ai/config.json",
     "instructions": ["obsidian-brain-instructions 1.md"]
   }
   ```

3. If you use another harness that doesn't read `AGENTS.md`, also add a one-line pointer so it loads these instructions:
   - Claude Code: `CLAUDE.md` in the root, containing `@AGENTS.md`.
   - GitHub Copilot: `.github/copilot-instructions.md`, containing "Follow AGENTS.md in the workspace root, including its Brain section, in every session."
   - Cursor: `.cursor/rules/brain.mdc` with `alwaysApply: true` in its front matter and the same sentence.
4. Start any agent session. It sets up the brain on its first run and asks you a few questions.
5. Optional: open `brain/` as a vault in Obsidian (Open folder as vault) to browse the notes and the graph.

You don't need to do anything else. The brain fills in as you work.

## First run (agents)

If `brain/` doesn't exist, or is missing any file below, create what's missing before the user's task, then carry on with the task.

1. Ask the user, in one message: their name, their role and team, what they mostly work on, and the time zone for diary timestamps. If they don't answer, use "the owner" and UTC (Coordinated Universal Time), and fill the gaps later.
2. Create this layout:

```
brain/
├── INDEX.md                 ← one table row per note: name | when to use | path
├── Home.md                  ← map of content, links to every topic note
├── Owner.md                 ← who the owner is, their role, team and time zone
├── daily-log/
│   ├── status.md            ← rolling snapshot: current focus, open items, waiting on
│   └── YYYY-MM-DD.md        ← one file per day
└── Working/
    ├── Tickets and recent work.md
    ├── How I work.md        ← the owner's preferences and corrections
    ├── Environments.md      ← URLs, environments, repo paths
    └── Gaps.md              ← things we don't know yet
```

3. Seed each file with a title, one line saying what it holds, and `Created YYYY-MM-DD`. Fill `Owner.md` from the answers. Add every note to `INDEX.md` and link it from `Home.md`.
4. Write today's diary with a first bullet: `- HH:MM <TZ>: Brain created.`
5. If the workspace is a git repository, the brain lives in it and is committed like any other file (see "Publishing"). Add `brain/.obsidian/workspace.json` to `.gitignore`.

## Every session

**Start.** Before the task:
1. Read `brain/daily-log/status.md`, then today's `daily-log/YYYY-MM-DD.md` if it exists.
2. Read `brain/INDEX.md` and open only the notes that match the task. Follow `[[wikilinks]]` from there. Never scan the whole vault.
3. Apply what you find, especially `Working/How I work.md`.

**During.** Log as you go, not only at the end, so a session that stops early still leaves a record:
- After each meaningful step (a decision, a finished change, a merge, a blocker, an answer from someone, something learned), append one bullet to today's diary.
- When the owner corrects you or states a preference, add it to `Working/How I work.md` straight away, with the date.

**End.** Before you report back:
1. Put each durable finding in its note ("Where things go").
2. Rewrite `daily-log/status.md` so it is true now: current focus, open items, what's waiting on whom. Replace stale lines; don't append history there.
3. If you created a note, add its `INDEX.md` row and `Home.md` link.

## Daily diary

- One file per day: `brain/daily-log/YYYY-MM-DD.md`, in the owner's time zone. Create it with a `# YYYY-MM-DD` heading if it's missing.
- One timestamped bullet per event: `- 14:05 ET: Finished the login retry in the local repo. Next: update status.md.`
- Say what happened and what's next, and name things fully (what changed, which local path, and who was involved).
- Log real work even when it was small. Skip pure chatter.
- Several sessions may write the same day. Append only; never rewrite or reorder other entries.
- Write by absolute path. A session may run in a git worktree or a subfolder, not the main checkout.
- Don't add an `INDEX.md` row per day. `status.md` is the way in.

## Where things go

| Happened | Update |
|----------|--------|
| Real work or learning in a session | Append today's diary and refresh `daily-log/status.md` |
| New understanding of a system, integration or domain | Patch that topic note, or create one + `INDEX.md` row + `Home.md` link |
| A ticket, project or recurring theme | `Working/Tickets and recent work.md`, or a project note of its own once it grows |
| A project's status changed | That project's note: keep a dated "Current status" at the top and demote the old one to "Previous status" |
| The owner's preference, correction or habit | `Working/How I work.md` |
| URL, environment or repo path | `Working/Environments.md` |
| Found something we don't know | Add a line to `Working/Gaps.md` |
| Filled a known gap | Remove its line from `Working/Gaps.md` |
| A fact turned out wrong | Edit it in place. Don't leave the old version. |

## Note conventions

- Wikilinks (`[[Note name]]`) are the graph. Link to a note instead of repeating it. Tags are secondary.
- One idea per note, with a clear title. Short bullets over essays.
- Date what you add or confirm (`Last reinforced YYYY-MM-DD`). A dated, stale note beats a missing one.
- Say when something is inferred rather than confirmed.
- Folders are for browsing only. Every note should be reachable from `Home.md` by links.
- Never put secrets in the brain: passwords, tokens, keys, connection strings. Say where a secret lives instead.
- Don't copy shared team docs into the brain. Link to them.

## Publishing

Only if the workspace is a git repository, and only on this machine:
- Commit only when the person using this workspace asks. Record that answer in `Working/How I work.md`.
- Look at the whole diff first. Keep other sessions' edits; never discard them.
- Commit note files only, never `.obsidian/workspace.json`.
- Do not add a remote, pull, or push. This copy stays local.
- Never switch branches in a checkout that has uncommitted work.
- If a commit cannot be made, leave the work in place and say exactly what blocks it.

_Fuente: [Knowledge/referencias/obsidian-brain-instructions 1.md](Knowledge/referencias/obsidian-brain-instructions%201.md) (licencia MIT)._
