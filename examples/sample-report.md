# Sample FontPlaybook Report

This is the kind of decision report FontPlaybook asks an AI coding agent to produce before it changes typography.

## Typography Direction

- Site type: trust-heavy fintech landing page
- Current issue: generic system font, weak heading/body contrast, and no clear role for numbers or CTAs
- Recommended direction: use one trustworthy UI sans across the interface, then create premium feel through weight, spacing, and a tighter hero heading

## Options

1. Best fit: IBM Plex Sans
   - Use for: body, nav, buttons, tables, hero, product UI
   - Why: institutional, technical, confident, strong numerals
   - Watch-outs: can feel serious; needs warm color/spacing to avoid looking too corporate

2. Safe fit: Public Sans
   - Use for: body, forms, account flows, dashboards
   - Why: sober, legible, familiar, strong for regulated or public-service interfaces
   - Watch-outs: less distinctive for a marketing hero

3. Bold fit: Space Grotesk headings + Inter body
   - Use for: H1/H2 and large marketing moments, with Inter for everything else
   - Why: gives the hero a memorable voice while keeping UI text readable
   - Watch-outs: use the display face sparingly; not ideal for dense banking UI

## Implementation

- Load: only `400`, `500`, `600`, and `700`
- Body: `16px`, `1.55` line-height
- Hero heading: `clamp()` with bounded sizes, `1.05` line-height, `-0.03em` letter-spacing
- Fallbacks: system sans stack after the custom family
- Verification: inspect computed fonts and test mobile wrapping
