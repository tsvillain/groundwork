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
- **update**: at session end, appends to PROGRESS and ticks TASKS so the docs never go stale.

Just ask: "plan a new project", "where was I on this?", or "wrap up the session".

## Install

The skill folder must be named `groundwork`.

**Claude Code**

```sh
git clone https://github.com/tsvillain/groundwork.git ~/.claude/skills/groundwork
```

For one project only, clone into `.claude/skills/groundwork` in that repo instead.

**Codex**

```sh
git clone https://github.com/tsvillain/groundwork.git ~/.agents/skills/groundwork
```

For one project only, clone into `.agents/skills/groundwork` in that repo instead. Restart Codex if the skill does not appear.

**Cursor**

```sh
git clone https://github.com/tsvillain/groundwork.git ~/.cursor/skills/groundwork
```

Cursor also loads `~/.agents/skills/`, so one clone there serves both Codex and Cursor. For one project only, use `.cursor/skills/groundwork` or `.agents/skills/groundwork` in that repo.

**Other agents**: clone into the agent's skills directory.

## Layout

```
SKILL.md      instructions the agent follows
templates/    AGENTS.md, PRD.md, ARCHITECTURE.md, DESIGN.md, TASKS.md, PROGRESS.md, ROADMAP.md, MARKETING.md
```

## License

[MIT](LICENSE)
