# Evaluation criteria

Pass or fail, never "looks good". Each criterion names what to check and how, so a
failure can be turned into a specific fix.

Use: copy the applicable criteria into your working notes **before** looking at the
output. Criteria written after the fact bend toward whatever is already on screen.

Items marked (house rule) are this skill's own heuristics, not external standards.
Change them freely.

## Hierarchy
- [ ] Squint test: step back or blur the screenshot. The first thing the eye lands on is the intended one (name which).
- [ ] Display text is at least 3x body size. (house rule)
- [ ] At most one primary action per viewport.

## Spacing and alignment
- [ ] Every margin, padding and gap comes from the spacing scale. Search the CSS for `px` values that are not in `tokens.md`.
- [ ] Left edges of text and blocks align to a few named axes (list them).
- [ ] Related elements are closer together than unrelated ones (at most 16px vs at least 48px).

## Typography
- [ ] At most 2 families plus mono, at most 4 sizes in one view.
- [ ] Body text is at least 16px with 60 to 72 characters per line.
- [ ] No more than 2 weights in use.

## Color and contrast
- [ ] Text contrast is measured, not eyeballed: at least 4.5:1, or 3:1 for text of 24px or more (18.66px or more if bold).
- [ ] Accent covers under about 5% of the viewport. (house rule)
- [ ] Nothing is communicated by color alone (links, errors, status).

## Consistency
- [ ] The same component has the same radius, padding and state behavior everywhere.
- [ ] No color, size or spacing value outside `tokens.md`.

## Responsive
- [ ] 375px: no horizontal scroll, touch targets at least 44px, text at least 16px.
- [ ] 768px: layout is intentional, not a stretched phone layout or a squashed desktop one.
- [ ] 1440px: content stays inside `--container`, lines do not stretch.

## Content
- [ ] No lorem ipsum. Every heading says something specific to this product.
- [ ] Invented copy is listed as placeholder in the report.

## Interaction and accessibility
- [ ] Every interactive element has a visible focus style and a sensible tab order.
- [ ] `prefers-reduced-motion` is respected.
- [ ] Images have `alt`, icon-only controls have accessible names.

## Anti-pattern sweep
- [ ] None of the patterns in `anti-patterns.md` is present.

## Critique format

Report only failures, one line each:

| Criterion | Observed | Fix |
| --- | --- | --- |
| Spacing scale | feature grid gap is 20px, not in scale | change to `--space-5` (24px) |
