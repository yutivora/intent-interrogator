---
name: intent-interrogator
description: >
  Forces structured design questions before generating any UI, landing page,
  component, or visual artifact. Use when the user asks to build, design,
  create, make, or generate anything visual — websites, dashboards, apps,
  landing pages, components, emails, or brand assets — and the request
  lacks specific direction on feeling, audience, or constraint. Prevents
  the agent from defaulting to generic AI-generated patterns.
---

# Intent Interrogator

## When to activate

Activate BEFORE writing any code or generating any design artifact when:

- The user asks to "build," "design," "create," or "make" something visual
- The request describes *what* to build but not *how it should feel*
- The user uses vague aesthetic language: "make it look nice," "modern,"
  "clean," "professional," "sleek"
- No audience, tone, or constraint has been specified

Do NOT activate when the user has already provided a detailed brief with
audience, tone, constraints, and success criteria.

## What to do

1. Ask 4 questions, one at a time. Do not bundle them.
2. Wait for each answer before asking the next.
3. After all 4 answers, produce a short Design Intent Brief (see format below).
4. Ask the user to confirm or correct the brief.
5. Only after confirmation, begin generating the artifact.

## The 4 questions

Ask these in order. Adapt the wording to the context, but keep the intent.

### Question 1 — Feeling

"In the first 3 seconds of seeing this, what should a person feel?
For example: calm, impressed, curious, reassured, energised, exclusive,
trustworthy, playful, serious, warm, minimal, bold.
Pick 2–3 words."

### Question 2 — Audience

"Who is the specific person this is for? Not 'users' — describe one
real person. What are they doing when they encounter this?
What do they care about? What frustrates them?"

### Question 3 — Constraint

"What is the single most important constraint I should respect?
For example: it must feel like our existing brand, it must work on
mobile first, it must load in under 2 seconds, it must be accessible
to screen readers, it must not look like a typical SaaS template."

### Question 4 — Anti-pattern

"What should this definitely NOT feel like or look like?
What would make you say 'that's wrong'?
For example: generic, corporate, cluttered, childish, too minimal,
like every other AI-generated site, like a template."

## Output format — Design Intent Brief

After the 4 answers, produce a short brief in this exact shape:

    ## Design Intent Brief

    **Feeling:** [2–3 words from Q1]
    **Audience:** [1–2 sentences from Q2]
    **Primary constraint:** [1 sentence from Q3]
    **Anti-pattern:** [1 sentence from Q4]

    **Implication for execution:**
    - Typography: [derived choice]
    - Colour: [derived choice]
    - Layout: [derived choice]
    - Motion: [derived choice]
    - Copy tone: [derived choice]

Then ask: "Does this capture it? Anything to adjust before I build?"

## Rules

- Never skip the questions, even if the request seems clear.
- Never generate the artifact before the brief is confirmed.
- If the user gives a one-word answer, ask one follow-up to deepen it.
- If the user says "just build it," acknowledge their time pressure and
  say: "I'll ask 2 quick questions instead of 4 so I don't guess wrong."
  Then ask Q1 and Q4 only.
- The brief becomes a constraint the agent must respect for the rest
  of the session.