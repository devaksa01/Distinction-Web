# Anti-patterns

Patterns that mark output as generic. Format for every entry:

- **Why it reads generic**: the default it comes from
- **Instead**: a concrete replacement

Every ban needs a replacement. A ban alone makes the model jump to the next most likely
default that is not yet banned. Keep this list to your own taste: delete entries you
disagree with, add the ones you keep seeing.

### AP-01 Purple-to-blue gradient fields
- **Why it reads generic:** the most common "modern" background in generated pages.
- **Instead:** one flat color from `tokens.md`. Create depth with a `--paper-2` block or a hairline rule.

### AP-02 Emoji as icons
- **Why it reads generic:** it is the cheapest substitute for a designed icon.
- **Instead:** inline SVG icons with one consistent stroke width, or typographic marks (numerals, arrows, section signs).

### AP-03 Rounded card plus soft shadow on everything
- **Why it reads generic:** every block becomes the same object, so nothing has rank.
- **Instead:** group with whitespace and 1px rules. Use a card only when the content is a discrete object (a product, a person, a plan).

### AP-04 Hero, three feature cards, CTA
- **Why it reads generic:** the layout is chosen before the content is known.
- **Instead:** design from the content. Lead with one dominant statement, then let the content decide the structure (a table, a timeline, a single large figure).

### AP-05 Everything centered
- **Why it reads generic:** centering removes the reading axis and the hierarchy with it.
- **Instead:** left-aligned text on a shared axis, with a deliberate asymmetric layout.

### AP-06 Gradient text on headings
- **Why it reads generic:** decoration standing in for type choice.
- **Instead:** solid `--ink`. Let size and the display font carry the heading.

### AP-07 Glassmorphism and blur panels
- **Why it reads generic:** a visual effect without a reason tied to the content.
- **Instead:** opaque surfaces. Reserve blur for a sticky header over scrolling content, and only if it improves legibility.

### AP-08 One font for everything at similar sizes
- **Why it reads generic:** the same family at 14 to 20px on every element gives flat hierarchy.
- **Instead:** use the display/body pair from `tokens.md` and a display size at least 3x the body.

### AP-09 Slogan copy with no claim
- **Why it reads generic:** "Elevate your workflow" fits any product, so it says nothing about this one.
- **Instead:** a specific claim with a noun and a number ("Invoices paid in 9 days on average").

### AP-10 Hover scale-up on every interactive element
- **Why it reads generic:** it is the default hover effect and signals nothing.
- **Instead:** change color or underline on hover, use motion only where it explains a state change.

### AP-11 Sections of identical height and padding
- **Why it reads generic:** uniform rhythm reads as a template with no emphasis.
- **Instead:** vary section density on purpose: one tight block, one with generous space around a single statement.
