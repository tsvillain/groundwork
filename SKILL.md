---
name: groundwork
description: Interview the user and write lean planning docs (AGENTS.md, PRD, ARCHITECTURE, DESIGN, TASKS, PROGRESS, ROADMAP, MARKETING) before a new project, then keep them current. Use when starting, planning, scoping or kicking off any new project (side project, startup, client work, team repo); when resuming a project or asking where things stand and what to do next; and at the end of a work session to update progress and tick off tasks.
license: MIT
---

# Groundwork

Plan once, then let the docs carry context between sessions and between agents.
The interview is the product: sharp questions produce docs worth following.
Templates live in `templates/`, next to this file.

## The doc set

| File | Job | When to read |
|------|-----|--------------|
| `AGENTS.md` (project root) | Rules for agents plus an index of the docs | Every session |
| `docs/PROGRESS.md` | Log: done, broke, next | Every session |
| `docs/TASKS.md` | Small steps for the current milestone only | Every session |
| `docs/PRD.md` | What it is, for whom, non-goals | When a task touches scope |
| `docs/ARCHITECTURE.md` | Stack, folders, data flow | When a task touches structure |
| `docs/DESIGN.md` | Colors, fonts, components, vibe | When a task touches UI |
| `docs/ROADMAP.md` | Milestones and phases | When picking the next milestone |
| `docs/MARKETING.md` | Audience, positioning, voice | When writing public copy |

ROADMAP holds milestones. TASKS holds only the current milestone's steps. PROGRESS records what happened. Do not let them overlap.

## Scale to the project

Ask how big the project is before writing anything. Create only what fits:

- **Tiny** (weekend toy, script, experiment): AGENTS.md, PROGRESS.md, TASKS.md. Fold a two-line "what and why" into AGENTS.md instead of a PRD.
- **Small** (useful tool, few weeks): add PRD.md and ARCHITECTURE.md. Add DESIGN.md only if it has a UI.
- **Serious** (product, public launch, users who are not you): the full set, including ROADMAP.md and MARKETING.md.

Skip a doc rather than fill it with guesses. It can be added later when the need is real.

## Modes

Pick the mode from the request. If unclear, check for `docs/PROGRESS.md`: missing means init, present means resume.

### init: interview, then write

Ask a few questions at a time, not all at once. Push back on vague answers until each is concrete enough to build from.

1. **Who is it for?** One specific person or group. Push back on "everyone", "developers", "people who want X": ask who would use it this week and why.
2. **What is the core loop?** The one thing a user does repeatedly, step by step. Push back on feature lists: ask which single flow must work for this to be worth shipping.
3. **What does done look like for v1?** Push back on open-ended scope: ask what can be cut and still be useful.
4. **What are the non-goals?** At least two things it will not do. Push back on "none": every project has tempting scope to refuse.
5. **What stack?** Language, framework, data store, hosting. Push back on "whatever is best": recommend one choice with a reason, and ask for a yes or no.
6. **What is the vibe?** (UI projects) Three adjectives plus one product it should feel like. Push back on "clean and modern": ask what it must not look like.
7. **What must an agent never do?** Things like adding dependencies without asking, touching certain files, or skipping tests.
8. **How big is it?** Tiny, small or serious, per the scaling rule above.

For serious projects, also ask for milestones (ROADMAP) and the audience, competitors and voice (MARKETING).

Then write the docs:

- Copy each chosen template into place: `AGENTS.md` at the project root, everything else in `docs/`.
- Replace every guidance line with real content from the interview. Delete sections that do not apply. Leave no placeholders.
- Keep the prefilled "How to build" rule in AGENTS.md by default; the user may edit or drop it.
- Write TASKS.md as small steps for the first milestone only, each finishable in one sitting.
- Start PROGRESS.md with one entry: the docs were created.
- If the project already has an `AGENTS.md` or `CLAUDE.md`, merge: keep existing content, add the rules and the docs index as new sections, and never overwrite or delete what is there. If only `CLAUDE.md` exists, add the docs index to it and ask before creating `AGENTS.md` beside it.
- Show the user a short summary of what was written and ask for corrections.

### resume: say where things stand

1. Read `AGENTS.md`, `docs/PROGRESS.md` and `docs/TASKS.md`. Nothing else yet.
2. Tell the user in a few lines: what was last done, what is broken or open, what is next.
3. Pick the next unticked task and confirm it with the user before starting.
4. Open PRD, ARCHITECTURE, DESIGN, ROADMAP or MARKETING only when the chosen task needs them.

If TASKS.md is fully ticked, read ROADMAP.md, propose the next milestone's tasks, and replace TASKS.md with them after the user agrees.

### update: after each task and at wrap-up

Run after each finished task (offer it) and whenever the user says they are wrapping up. Docs that go stale are worse than no docs.

1. Append a dated entry to `docs/PROGRESS.md`: done, broke, next. Keep it short and concrete. Never rewrite past entries.
2. Tick finished items in `docs/TASKS.md`. Add newly discovered steps. Remove steps that no longer make sense, and note why in PROGRESS.
3. If a decision changed the stack, scope or design, update the matching doc in the same pass and append a dated line to its Decisions section: `- YYYY-MM-DD: what changed - why`. Never delete past decision lines; mark superseded ones `(superseded YYYY-MM-DD)`.
4. If an agent rule was learned the hard way, add it to `AGENTS.md`.
5. Tell the user in one or two lines what changed in the docs.

## Rules for writing the docs

- Short and scannable: bullets over prose, one idea per line.
- Specific over generic: "Postgres 16 on Fly.io", not "a database".
- Every doc earns its place. If nobody will read it, do not write it.
