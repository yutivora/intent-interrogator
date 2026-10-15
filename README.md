# Intent Interrogator

A cross-agent skill that forces structured design questions before
generating any UI — and then verifies the output against those answers
to prevent design drift.

Works with Claude Code, OpenAI Codex CLI, Cursor, Gemini CLI, GitHub
Copilot, Windsurf, and any agent that follows the open Agent Skills
standard.

## The problem

AI agents default to the statistical average of their training data.
When you ask for a website or a component without giving specific
direction, you get the same patterns everyone else gets.

Even when you *do* give direction, the agent often forgets it halfway
through the build. The final result drifts away from what you asked for.

## How it works (3 phases)

1. **Interrogate** — Asks four questions about feeling, audience,
   constraint, and anti-pattern before generating anything.
2. **Persist** — Saves the agreed brief to `.intent/[project].md` so
   it survives across sessions, contributors, and agents.
3. **Verify** — Before declaring the work done, the agent compares the
   output against the brief and produces an **Intent Receipt** showing
   exactly where the design matched and where it drifted.

## Why this is different

Other skills ask questions once. This one keeps the answers alive:

- The brief is written to a file that travels with your repo.
- The agent checks the final output against the brief before saying "done."
- You get a shareable Intent Receipt that shows what matched and what drifted.
- Non-designers (founders, PMs, developers) can read the receipt and
  immediately understand whether the output matched the request.

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

The agent will:

1. Ask four questions about feeling, audience, constraint, and anti-pattern.
2. Write the agreed brief to `.intent/landing-page.md`.
3. Build the page.
4. Produce an Intent Receipt showing what matched and what drifted.

## The four questions

1. **Feeling** — what should the user feel in the first 3 seconds?
2. **Audience** — who specifically is this for?
3. **Constraint** — what's the one thing I must respect?
4. **Anti-pattern** — what should this definitely NOT look like?

## The Intent Receipt

After the work is done, the agent produces a short report like this:

    ## Intent Receipt — Landing Page
    Generated: 2026-10-15 · Session: 1

    ### Stated Intent
    - Feeling: calm, trustworthy, editorial
    - Audience: freelancers checking invoices on mobile
    - Constraint: must feel like our existing brand
    - Anti-pattern: generic, corporate, cluttered

    ### What Was Built
    - Typography: serif headings + neutral sans body ✅ matches editorial intent
    - Colour: warm off-white, deep green accent ✅ matches calm intent
    - Layout: single-column, generous whitespace ⚠️ may feel sparse on mobile
    - Motion: subtle fade-ins ✅ matches calm intent
    - Copy tone: direct, no exclamation marks ✅ matches editorial intent

    ### Drift Detected
    ⚠️ Layout uses generous whitespace that the brief's "mobile-first"
    constraint may not support. The stated audience (freelancers on
    mobile) suggests a denser information layout.

    ### Open Questions
    - Should the agent re-read the brand guidelines before the next session?

This is the part that makes the skill useful to non-designers. You don't
need design vocabulary to see whether the output matched what you asked for.

## License

MIT