# Intent Interrogator

A cross-agent skill that forces structured design questions before
generating any UI — so the output isn't generic.

Works with Claude Code, OpenAI Codex CLI, Cursor, Gemini CLI, GitHub
Copilot, Windsurf, and any agent that follows the open Agent Skills
standard.

## The problem

AI agents default to the statistical average of their training data.
When you ask for a website or a component without giving specific
direction, you get the same patterns everyone else gets.

This skill intervenes before generation. It asks four questions
about feeling, audience, constraint, and anti-pattern, then produces
a Design Intent Brief that constrains the rest of the session.

## Install

Copy `SKILL.md` into your agent's skills directory:

| Agent | Path |
|---|---|
| Claude Code | `~/.claude/skills/intent-interrogator/SKILL.md` |
| OpenAI Codex CLI | `.agents/skills/intent-interrogator/SKILL.md` |
| Cursor | `.cursor/skills/intent-interrogator/SKILL.md` |
| Gemini CLI / Antigravity | `~/.gemini/antigravity/skills/intent-interrogator/SKILL.md` |
| Windsurf | `.windsurf/skills/intent-interrogator/SKILL.md` |
| GitHub Copilot | Reference via `.github/copilot-instructions.md` |

For project-level use, place `SKILL.md` in the equivalent
`<project>/.agents/skills/` or `<project>/.claude/skills/` directory.

## Usage

Just ask your agent to build something. The skill activates automatically
when the request lacks specific direction.

Example:

> Build me a landing page for a freelance accountant.

The agent will ask four questions, produce a brief, and only then
start building.

## The four questions

1. **Feeling** — what should the user feel in the first 3 seconds?
2. **Audience** — who specifically is this for?
3. **Constraint** — what's the one thing I must respect?
4. **Anti-pattern** — what should this definitely NOT look like?

## License

MIT