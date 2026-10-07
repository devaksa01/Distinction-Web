<!-- DW:EXAMPLE  Entries below are fictional and their files do not exist. Replace them with your own, then delete this line. -->
# Reference index

One entry per screenshot. The annotations are the point of this file: the model sees
pixels, so it needs to be told which part of an image you care about and which part to ignore.

## Conventions

- File name: `<kind>-<source>-<dimension>.png`, for example `hero-linear-type.png`.
- One dimension per file: `type`, `layout`, `color`, `motion` or `component`.
- Capture at 1440px wide. Add a second file ending in `@375` only if mobile behavior is part of what you like.
- Choose 3 to 5 references that agree with each other. References in clashing styles get averaged into a generic result.
- Screenshots belong to their owners. They are git-ignored and never published. Only this INDEX is.

## Entry format

```
### <file name>
- Source: <URL>, captured <date>
- Dimension: type | layout | color | motion | component
- Take: <the specific principle to learn from>
- Avoid: <what in the image must NOT be copied>
- Measured: <real values from DevTools, if relevant>
```

## Entries

### hero-example-type.png
- Source: https://example.com, captured 2026-10-07
- Dimension: type
- Take: very large serif headline, tight tracking, a lot of empty space above it. The scale contrast does the work.
- Avoid: the gradient background, the 3D illustration on the right.
- Measured: h1 96px / line-height 1.05 / letter-spacing -0.02em, body 16px.

### button-example-component.png
- Source: https://example.com/pricing, captured 2026-10-07
- Dimension: component
- Take: flat button with a hard 1px border, color inversion on hover, no shadow.
- Avoid: the pill shape, the arrow icon animation.
- Measured: height 40px, padding-inline 24px, transition 120ms.
