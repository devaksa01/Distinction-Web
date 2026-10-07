---
name: distinction-web
description: Use when building, redesigning, or polishing web UI (landing pages, hero sections, components such as buttons and cards, full pages) so the result follows one specific, opinionated visual taste instead of generic AI defaults. Supplies design tokens, anti-patterns with replacements, annotated references, and an evaluation checklist. Skip for backend work, non-visual code, or non-web design.
---

# Distinction Web

A taste layer for web UI work. It does not replace a client's brand. It constrains the
choices Claude would otherwise make from statistical defaults.

This file is a router. Keep it short. Detail lives in the other files and is read only
when the step below says so.

## Precedence

1. The user's current request.
2. Project-level design files (brand guide, tokens, `DESIGN.md`, existing CSS variables).
   These carry brand identity.
3. This skill. It carries taste and process, and fills gaps the project leaves open.

If a project defines its own palette or fonts, use those and still apply this skill's
principles: hierarchy, spacing rhythm, anti-patterns, evaluation.

## Step 0: Placeholder guard

Some files ship as templates and contain the marker `DW:EXAMPLE`. Check `tokens.md`,
`components.md` and `references/INDEX.md` for it. If any file still has the marker, tell
the user which files are unfilled and ask whether to continue with the example values or
wait. Never treat example values as the user's real taste without saying so.

## Step 1: Brief

Before any code, write the brief in three lines: audience, intended feeling, real content
available. If one is unknown and the answer would change the design, ask (at most 3
questions). Otherwise state the assumption and continue. Layout should be designed around
content. Without content it collapses into the generic template.

## Step 2: Constraints

Read `tokens.md`. When building components, also read `components.md`.

- Declare every value as a CSS custom property in one place and reference only those.
- No hard-coded hex colors, font sizes, or spacing outside the scales.
- If a needed value is missing, add it to the token block with a one-line reason. Do not inline it.

## Step 3: References

Read `references/INDEX.md`.

- Choose at most 3 entries, each for a different dimension (type, layout, color, motion, component).
- Open an image file only for a chosen entry. If the file is missing, skip the entry and say so.
- Follow the entry's `Take` line and obey its `Avoid` line.
- Take the principle, never the arrangement. Do not reproduce a reference's layout wholesale.
- If no entry fits, say so and work from tokens alone. Do not invent a reference.

## Step 4: Anti-patterns

Read `anti-patterns.md` before writing code. Use the listed replacement for each banned
pattern. If you notice yourself reaching for a banned pattern, that is the default
talking: stop and use the replacement.

## Step 5: Build

Use real content. If the user has none, write specific copy (concrete nouns, numbers,
claims). No lorem ipsum, no slogans like "Elevate your workflow". Flag invented copy as
placeholder in the final report.

## Step 6: Verify visually

Read `evaluation.md`. Copy the criteria that apply into your working notes before you
look at the result, so the criteria are not shaped by the output.

1. Render the page and screenshot at 1440px and 375px wide, if a browser or Playwright is available.
2. Mark each criterion pass or fail with a concrete observation
   ("card gap is 12px in one row and 20px in the next", not "spacing feels off").
3. Fix only the failed criteria, re-render, repeat. Maximum 3 loops.

If you cannot render, say so, review the code against the criteria, and do not claim
visual verification.

## Step 7: Report

Keep it short: which tokens and references were used, which criteria still fail, which
copy is placeholder.
