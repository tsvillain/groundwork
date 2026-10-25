<h1 align="center">groundwork</h1>
<p align="center">
  <a href="LICENSE"
    ><img
      alt="License: MIT"
      src="https://img.shields.io/badge/license-MIT-green?style=flat-square"
  /></a>
  <a href="https://agentskills.io"
    ><img
      alt="Works with Claude Code, Codex, Cursor"
      src="https://img.shields.io/badge/works%20with-Claude%20Code%20%7C%20Codex%20%7C%20Cursor-blue?style=flat-square"
  /></a>
  <a href="https://github.com/tsvillain/groundwork/stargazers"
    ><img
      alt="GitHub stars"
      src="https://img.shields.io/github/stars/tsvillain/groundwork?style=flat-square"
  /></a>
</p>

<h3 align="center">Plan once. Pick up any project where you left off.</h3>

<p align="center">
  <img alt="groundwork - plan once, pick up any project where you left off" src="assets/banner.avif" width="100%" />
</p>

## What it is

Start a new project with an AI agent and no plan, and the agent guesses: the stack, the scope, the look, what done means.
It does not matter whether it is a side project, a startup, client work or a team repo.
And every new session starts from zero: switch between projects or step away for a week, and the first question is always "where was I?".

groundwork fixes that before the first line of code.
It interviews you once, pushes back until the answers are concrete, and writes a small set of planning docs sized to the project.
From then on, you and any agent read the same docs: a short core every session, the rest only when a task needs it.
After each task, the docs get updated, so they never go stale.

groundwork is not an app and not a CLI.
It is a portable [Agent Skill](https://agentskills.io): a `SKILL.md` plus templates that any agent supporting the open standard can follow.

## Features

- **An interview that pushes back** - asks who it is for, the core loop, v1 scope, non-goals, stack and vibe, and refuses "everyone" or "clean and modern" as answers.
- **Scales to project size** - a weekend toy gets three docs; a serious product gets all eight.
- **Always-read core, on-demand detail** - agents read `AGENTS.md`, `PROGRESS.md` and `TASKS.md` every session, and open the PRD, architecture, design, roadmap or marketing docs only when a task needs them.
- **Resume** - "where was I?" gets what was done, what broke, and the next task.
- **Update after each task** - the agent offers to log progress and tick tasks after every finished task, and runs it when you wrap up.
- **First-principles build rule** - every generated `AGENTS.md` tells agents to state the real problem, question inherited patterns, and build the simplest thing that fits; edit or drop it.
- **Merges, never overwrites** - an existing `AGENTS.md` or `CLAUDE.md` keeps its content; groundwork adds its rules and docs index alongside.
- **Works with any Agent Skills agent** - Claude Code, Codex, Cursor and others.

## Quick Start

### Requirements

- An agent that supports Agent Skills: Claude Code, Codex, Cursor or others.
- Node.js 22.20+ for the one-command install, or Git for the manual one.

### Install

```sh
npx skills add tsvillain/groundwork -g
```

This uses the open [`skills`](https://github.com/vercel-labs/skills) CLI. It detects your installed agents (Claude Code, Codex, Cursor and many more) and asks which to install to. Drop `-g` to install into the current project only. To skip the prompt, name the agents: `-a claude-code -a codex -a cursor`.

**Manual fallback**: clone into your agent's skills folder; the folder must be named `groundwork`.

```sh
git clone https://github.com/tsvillain/groundwork.git ~/.claude/skills/groundwork  # Claude Code
git clone https://github.com/tsvillain/groundwork.git ~/.agents/skills/groundwork  # Codex and Cursor
```

### Talk to it

```sh
> plan a new project: a booking app for a client's physio clinic

# groundwork asks a few questions at a time, and pushes back:

  Who is it for? "Clinics" is too broad - who books, and who manages the schedule?

> patients booking 30-minute slots on their phones; two physios managing their own calendars

# ...a few answers later it writes AGENTS.md and docs/, sized to the project.
# Next week, in a fresh session:

> where was I on this?

  Done: slot picker. Broke: timezones in reminder emails. Next: physio calendar view. Start it?
```

## How It Works

```
                 you
                  │  "plan a new project"
                  ▼
 ┌─────────────────────────────────────┐
 │ init: the interview                 │
 │ who, core loop, v1, non-goals,      │
 │ stack, vibe, never-dos, size        │
 └──────────────────┬──────────────────┘
                    ▼
 your-project/
 ├── AGENTS.md            rules + docs index      always read
 └── docs/
     ├── PROGRESS.md      done, broke, next       always read
     ├── TASKS.md         current milestone       always read
     └── PRD, ARCHITECTURE, DESIGN,               on demand
         ROADMAP, MARKETING
                    │
                    ▼
 ┌─────────── every agent session ─────────────┐
 │                                             │
 │   resume ──► build one task ──► update ──┐  │
 │     ▲                                    │  │
 │     └────────────────────────────────────┘  │
 └─────────────────────────────────────────────┘
```

**init** interviews you and writes only the docs that fit.
**resume** reads the core docs, says where things stand, and picks the next task.
**update** appends to `PROGRESS.md` and ticks `TASKS.md` after each finished task (offered) or when you wrap up.

## The doc set

`AGENTS.md` goes at the project root (most agents load it automatically). Everything else goes in `docs/`.

| Always read, every session | Read on demand, when a task needs it |
|----------------------------|--------------------------------------|
| `AGENTS.md`: rules for agents plus an index of the docs | `PRD.md`: what you are building and for whom |
| `PROGRESS.md`: done, broke, next | `ARCHITECTURE.md`: stack, folders, data flow |
| `TASKS.md`: small steps for the current milestone | `DESIGN.md`: colors, fonts, components, vibe |
| | `ROADMAP.md`: milestones and phases |
| | `MARKETING.md`: audience, positioning, voice |

## Contributing

Contributions are welcome - see [CONTRIBUTING.md](CONTRIBUTING.md) for how to propose changes to the skill and its templates.

## License

MIT - see [LICENSE](LICENSE).

## Star History

<a href="https://www.star-history.com/?repos=tsvillain%2Fgroundwork&type=date&legend=top-left">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/chart?repos=tsvillain/groundwork&type=date&theme=dark&legend=top-left" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/chart?repos=tsvillain/groundwork&type=date&legend=top-left" />
   <img alt="Star History Chart" src="https://api.star-history.com/chart?repos=tsvillain/groundwork&type=date&legend=top-left" />
 </picture>
</a>
