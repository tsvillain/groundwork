# Contributing

groundwork is a `SKILL.md` plus `templates/`. Changes are welcome; keep them small and focused.

## Proposing a change

- Open an issue first for anything beyond a typo, so the idea can be discussed before you write it.
- `SKILL.md` holds the behavior: modes, interview, scaling rule, file placement. Keep it agent-neutral (no tool names from one agent) and lean; bulky content belongs in a template.
- `templates/` holds the docs the skill writes into a user's project. Each template is section headings with one-line guidance prompts: no lorem ipsum, no long prose. A new section has to earn its place in every project that uses it.
- If a change affects the doc set, modes or install, update `README.md` in the same change.

## Testing

There is no test suite. Test a change by using it:

1. Install your local copy into an agent, e.g. `npx skills add /path/to/your/groundwork -a claude-code` run from a scratch project, or symlink this folder into the agent's skills directory.
2. In a scratch project, ask the agent to plan a new project and run through init. Check the interview pushes back on vague answers and the docs it writes fit the project size.
3. Try resume ("where was I?") and update after a small task.
4. Validate the frontmatter with [skills-ref](https://github.com/agentskills/agentskills/tree/main/skills-ref): `skills-ref validate .`

## Commits

Use [Conventional Commits](https://www.conventionalcommits.org): `feat:`, `fix:`, `docs:`, `chore:` and so on, with a short subject.
