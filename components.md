<!-- DW:EXAMPLE  The Button spec is a sample. Replace it with your own rules, then delete this line. -->
# Components

One section per component, always in the same format so Claude can find the same
fields every time:

- **Purpose**: when to use it, and how many per view
- **Variants**: table of values, all taken from `tokens.md`
- **Sizes**
- **States**: default, hover, focus-visible, active, disabled, loading
- **Avoid**: what it must not become

Add new components by copying the Button section.

## Button

**Purpose:** triggers one action. At most one primary button per view.

**Variants**

| Variant | Background | Text | Border |
| --- | --- | --- | --- |
| primary | `--accent` | `--paper` | none |
| secondary | transparent | `--ink` | 1px `--ink` |
| text | transparent | `--ink` | none, underline with 4px offset |

**Sizes**

| Size | Height | Padding inline | Font |
| --- | --- | --- | --- |
| default | 40px (44px on touch viewports) | `--space-5` | `--step-0`, weight 500 |
| large | 48px | `--space-6` | `--step-1`, weight 500 |

Radius is `--radius-1`.

**States**
- hover: background shifts to `--ink` over `--dur-1` with `--ease`.
- focus-visible: 2px outline in `--ink`, 2px offset. Never remove the outline.
- active: `translateY(1px)`.
- disabled: opacity 0.4, `cursor: not-allowed`, `aria-disabled="true"`.
- loading: keep the button width fixed, swap the label for a small spinner, set `aria-busy="true"`.

**Avoid:** gradients, glow shadows, scale on hover, pill radius, icon-only buttons
without an accessible name, more than one primary button per view.
