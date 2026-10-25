# groundwork

An [Agent Skill](https://agentskills.io) that interviews you before a new project, writes a small set of planning docs, and keeps them current so you and any AI coding agent can pick the project back up after weeks away.

Works with any agent that supports the open Agent Skills format: Claude Code, Codex, Cursor and others.

## The doc set

`AGENTS.md` goes at the project root (most agents load it automatically). Everything else goes in `docs/`.

| Always read, every session | Read on demand, when a task needs it |
|----------------------------|--------------------------------------|
| `AGENTS.md`: rules for agents plus an index of the docs | `PRD.md`: what you are building and for whom |
| `PROGRESS.md`: done, broke, next | `ARCHITECTURE.md`: stack, folders, data flow |
| `TASKS.md`: small steps for the current milestone | `DESIGN.md`: colors, fonts, components, vibe |
| | `ROADMAP.md`: milestones and phases |
| | `MARKETING.md`: audience, positioning, voice |

Docs scale to the project: a weekend toy gets the three core files; a serious product gets all eight.

## Modes

- **init**: asks sharp questions (who it is for, the core loop, stack, vibe, non-goals), pushes back on vague answers, then writes only the docs that fit.
- **resume**: reads PROGRESS and TASKS, tells you where things stand, and picks the next task.
- **update**: after each finished task (offered) or when you wrap up, appends to PROGRESS and ticks TASKS so the docs never go stale.

Just ask: "plan a new project", "where was I on this?", or "wrap up the session".

## Install

```sh
npx skills add tsvillain/groundwork -g
```

This uses the open [`skills`](https://github.com/vercel-labs/skills) CLI (Node.js 22.20+). It detects your installed agents (Claude Code, Codex, Cursor and many more) and asks which to install to. Drop `-g` to install into the current project only. To skip the prompt, name the agents: `-a claude-code -a codex -a cursor`.

**Manual fallback**: clone into your agent's skills folder; the folder must be named `groundwork`.

```sh
git clone https://github.com/tsvillain/groundwork.git ~/.claude/skills/groundwork  # Claude Code
git clone https://github.com/tsvillain/groundwork.git ~/.agents/skills/groundwork  # Codex and Cursor
```

## Layout

```
SKILL.md      instructions the agent follows
templates/    AGENTS.md, PRD.md, ARCHITECTURE.md, DESIGN.md, TASKS.md, PROGRESS.md, ROADMAP.md, MARKETING.md
```

## License

[MIT](LICENSE)
