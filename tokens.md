<!-- DW:EXAMPLE  Values below are a sample taste. Replace them with your own, then delete this line. -->
# Design tokens

Source of truth for every visual value. Format: one block of CSS custom properties per
group, then rules that explain intent. The rules matter more than the numbers, because
they tell Claude what to do in cases the numbers do not cover.

How to fill this file: measure real values with browser DevTools (Computed tab, color
picker) from sites you like. Do not read numbers off screenshots, image-based estimates
drift.

## Intent

EXAMPLE: Warm, editorial, a little severe. Paper and ink with one hot accent used rarely.
Feels printed, not rendered.

## Color

```css
:root {
  --paper:   #F4F1EA; /* page background */
  --paper-2: #EAE5D8; /* alternate or raised sections */
  --ink:     #14130F; /* primary text */
  --muted:   #5E594F; /* secondary text */
  --accent:  #C93A14; /* one primary action per view, key emphasis */
  --rule:    #D8D2C4; /* hairlines and decorative dividers */
}
```

Contrast, computed with WCAG relative luminance:

| Pair | Ratio | Verdict |
| --- | --- | --- |
| ink on paper | 16.48 | all text |
| muted on paper | 6.17 | secondary text |
| muted on paper-2 | 5.53 | secondary text |
| accent on paper | 4.54 | passes AA for text, with almost no margin |
| paper on accent (button label) | 4.54 | use weight 500 or heavier |
| accent on paper-2 | 4.07 | large text and UI only, never body text |
| rule on paper | 1.34 | decorative only. Input borders use `--muted` or `--ink` |

Rules:
- One accent only. It covers under about 5% of any viewport.
- No dark mode is defined. Do not invent one, ask.
- No gradients. Depth comes from `--paper-2` blocks and rules.

## Typography

```css
:root {
  --font-display: "Instrument Serif", Georgia, serif;
  --font-body:    "Geist", system-ui, sans-serif;
  --font-mono:    "JetBrains Mono", ui-monospace, monospace;

  /* ratio 1.25 */
  --step--1: 0.8rem;
  --step-0:  1rem;
  --step-1:  1.25rem;
  --step-2:  1.563rem;
  --step-3:  1.953rem;
  --step-4:  2.441rem;
  --step-display: clamp(3rem, 7vw, 6rem); /* deliberately off-scale */

  --leading-tight: 1.05;
  --leading-body:  1.55;
  --tracking-display: -0.02em;
}
```

Rules:
- Display text is at least 3x the body size. The jump is what creates hierarchy.
- Two families plus mono. At most 4 distinct sizes in one view.
- Body text 16px minimum, line length 60 to 72 characters.
- Display weight 400 only. The serif carries the contrast, not boldness.

## Spacing

```css
:root {
  --space-1: 4px;   --space-2: 8px;   --space-3: 12px;  --space-4: 16px;
  --space-5: 24px;  --space-6: 32px;  --space-7: 48px;  --space-8: 64px;
  --space-9: 96px;  --space-10: 128px;
}
```

Rules:
- Related items sit at `--space-4` or less. Unrelated groups sit at `--space-7` or more.
- Section vertical padding is `--space-9` or more on desktop.

## Shape, borders, elevation

```css
:root {
  --radius-0: 0;
  --radius-1: 2px;
  --radius-pill: 999px;
  --border: 1px solid var(--rule);
  --shadow-overlay: 0 8px 24px rgb(20 19 15 / 0.12); /* menus and dialogs only */
}
```

Rules:
- Default radius is `--radius-1`. Pills are for tags only.
- No shadows on cards or buttons. Separate with rules and background shifts.

## Layout

```css
:root {
  --container: 1200px;
  --gutter: 24px;
}
```

Breakpoints (media queries cannot read custom properties, so they are stated here): 640px, 1024px, 1440px.
Twelve-column grid. Text blocks align to a shared left axis, avoid centering long text.

## Motion

```css
:root {
  --ease:  cubic-bezier(0.2, 0.7, 0.2, 1);
  --dur-1: 120ms;
  --dur-2: 200ms;
  --dur-3: 400ms;
}
```

Rules:
- Animate `opacity` and `transform` only.
- Respect `prefers-reduced-motion`.
- One orchestrated entrance sequence per page beats scattered hover effects.
