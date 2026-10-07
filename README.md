# Distinction Web

A Claude skill that makes AI-generated web design follow one specific taste instead of
statistical defaults.

## Why this exists

Left alone, a model picks the most probable answer to "make a good landing page", which is
the average of every landing page it has seen. That average is what people call AI slop.
This skill narrows the space of possible outputs with four things, in order of impact:

1. **Tokens and component rules** that constrain every visual value.
2. **Annotated references** that say what to take from an image and what to ignore.
3. **Anti-patterns with replacements** that block the common defaults.
4. **An evaluation loop** that makes Claude render, measure and fix against written criteria.

It is context plus a process. There is no magic in it, which means you can read all of it
and change all of it.

## How it works

A skill is a folder. Only `name` and `description` from `SKILL.md` are always in context.
The body of `SKILL.md` loads when a task matches, and the other files are read only when
a step in `SKILL.md` tells Claude to. This keeps context small, which matters because
instruction-following degrades when context is crowded with irrelevant material.

```
Distinction-Web/
  SKILL.md          router: precedence, 7 steps, when to read what
  tokens.md         color, type, spacing, shape, layout, motion
  components.md     per-component rules (example: Button)
  anti-patterns.md  banned defaults, each with a replacement
  evaluation.md     pass/fail criteria and the critique format
  references/
    INDEX.md        annotated reference entries (Take / Avoid / Measured)
    *.png           your screenshots (git-ignored, local only)
  README.md
  LICENSE
  .gitignore
```

## Install

Claude Code reads skills from a folder whose name matches the `name` in the frontmatter.
This repository is called `Distinction-Web`, the installed folder must be `distinction-web`.

- All projects: copy or link the folder to `~/.claude/skills/distinction-web/`
  (Windows: `%USERPROFILE%\.claude\skills\distinction-web\`)
- One project: `.claude/skills/distinction-web/` inside that repository

macOS or Linux, link instead of copy so edits apply immediately:

```bash
ln -s /path/to/Distinction-Web ~/.claude/skills/distinction-web
```

If the skill does not show up, start a new session. For other Claude surfaces, check the
current official documentation for how skills are uploaded.

## Make it yours (required)

The shipped content is a sample taste, marked with `DW:EXAMPLE`. Until you replace it,
the skill asks before using it.

1. `tokens.md`: replace the values. Measure them with DevTools from sites you like, do not estimate from screenshots.
2. `components.md`: rewrite the Button spec, then add components in the same format.
3. `references/`: add 3 to 5 screenshots named `<kind>-<source>-<dimension>.png` and one entry per file in `INDEX.md`. Write the `Take` and `Avoid` lines carefully, they are the most valuable part.
4. `anti-patterns.md`: delete what you disagree with, add what you keep noticing.
5. Delete the `DW:EXAMPLE` line from every file you have filled in.

## Use

Ask directly ("use distinction-web to build a pricing page for ...") or let it trigger
from the `description`. To test triggering, try 5 to 10 varied prompts, including some that
should not trigger it (a backend task, a non-web design). If it fires wrongly or not at all,
edit the `description` first.

## Client projects

Keep brand identity (logo, palette, tone) in each client's own repository. This skill holds
taste and process and stays the same across projects. The precedence order in `SKILL.md`
makes project files win over the skill when both define a value.

## Limits

- It cannot rescue a vague brief. Audience, feeling and real content still have to come from you.
- Models estimate numbers from images poorly. Precision lives in `tokens.md`, not in screenshots.
- If many people use the same skill unchanged, their outputs converge on its taste. Make it your own.
- Triggering depends on the `description`. It needs testing, not trust.

## License and credit

Licensed under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/). Full text in `LICENSE`.

You may share and adapt this material for non-commercial purposes if you give credit,
link the license, and indicate changes. Suggested credit line:

> Distinction Web by Devaksa01, licensed under CC BY-NC 4.0.

Reference screenshots are third-party work. They are not part of this repository and
are not covered by this license.
