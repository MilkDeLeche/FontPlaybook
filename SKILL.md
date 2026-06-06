---
name: font-playbook
description: Teach or guide Claude and AI coding agents to choose, load, pair, and apply fonts in webpages and web apps. Use when building or reviewing frontend typography, selecting UI fonts, creating CSS type systems, implementing Google Fonts/self-hosted/variable fonts, setting heading/body styles, improving readability, or replacing generic/default web-safe typography with a polished webpage font system.
---

# FontPlaybook

Use this skill to make typography decisions concrete in a webpage. Do not stop at naming a font; inspect the site context, identify what the current typography is failing to do, compare appropriate font directions, implement how the chosen family is loaded and tokenized, then check it in the UI.

## Core Workflow

1. Identify the page's purpose and reading conditions.
   - Product UI, dashboard, SaaS, docs, and forms need quiet, highly legible text fonts.
   - Editorial, portfolio, brand, and marketing pages can tolerate more expressive display type, but body text must stay easy to read.
   - Dense or data-heavy interfaces benefit from high x-height, clear numerals, many weights, and restrained contrast.

2. Audit the current template before recommending replacements.
   - Inspect existing CSS, HTML, framework theme files, design tokens, and imported fonts.
   - Identify whether the problem is the font family, incorrect loading, weak hierarchy, poor line-height, bad letter-spacing, low contrast, overuse of weights, or too many type styles.
   - If a font is intended but not appearing, debug loading before changing the design direction.

3. Choose one primary typeface first.
   - Prefer one family with enough weights before pairing fonts.
   - Use two families only when each has a clear role, such as expressive headings plus neutral body text, or sans UI plus monospace code.
   - Avoid using more than two non-system families on a single webpage.

4. Research real-world usage when it would improve confidence.
   - If internet access or a browser is available and the user wants recommendations, search for comparable sites, font specimens, foundry pages, Google Fonts pages, Typewolf, Fonts In Use, or brand/font documentation.
   - Look for examples from the same domain or adjacent quality bar: banks for finance, Stripe/Vercel/Linear-style references for product SaaS, editorial magazines for content-heavy pages, luxury brands for premium commerce.
   - Use real examples as evidence, not as commands to copy blindly.
   - Cite or summarize findings when sources are used.
   - If research is unavailable, say so and proceed from the local audit and the reference playbook.

5. Produce a recommendation set, not a single unexplained answer.
   - Offer a best-fit option for the user's stated goal.
   - Offer a safe/conservative option for trust, readability, and broad compatibility.
   - Offer a bolder option when the page has a hero, campaign, portfolio, or brand-forward surface.
   - For each option, state where it belongs: H1/H2, body, nav, buttons, captions, tables, numbers, code, or accents.
   - Include tradeoffs: personality, trust, readability, performance, licensing, and implementation complexity.

6. Check font quality before implementation.
   - Prefer families with at least 5 useful weights, ideally variable font support.
   - Confirm italics, punctuation, symbols, numerals, and required language coverage.
   - Favor screen-oriented UI fonts for body text.
   - Prefer open-source/free fonts for prototypes unless the project already has a licensed brand font.

7. Implement the font deliberately.
   - Load only the weights/styles actually used.
   - Use `font-display: swap` or equivalent hosted-font display behavior.
   - Define CSS custom properties for font families, weights, sizes, line-heights, and tracking.
   - Apply typography through semantic elements or reusable classes, not scattered one-off declarations.
   - Include strong fallbacks after every custom font.

8. Tune the type scale in context.
   - Start body text at `16px` for most webpages and product UIs.
   - Use body line-height around `1.5` to `1.75`; longer line lengths often need more line-height.
   - Use heading/display line-height around `1.0` to `1.25`.
   - Keep body letter-spacing at `0` unless a specific font requires correction.
   - Use slight negative letter-spacing only for large display headings, commonly `-0.01em` to `-0.04em`.
   - Keep paragraph measure comfortable, usually `60ch` to `75ch` for reading content.

9. Verify in the browser.
   - Inspect the computed font-family on body text, headings, buttons, inputs, and navigation.
   - Check loading behavior on refresh so the page does not visibly jump or render invisible text.
   - Test desktop and mobile widths.
   - Ensure buttons, labels, nav items, and cards do not overflow with the chosen font.

## Recommendation Format

When asked which fonts best work for a site, provide a compact decision report:

```markdown
Typography direction:
- Site type:
- Current issue:
- Recommended direction:

Options:
1. Best fit: Font Name
   - Use for:
   - Why:
   - Watch-outs:

2. Safe fit: Font Name
   - Use for:
   - Why:
   - Watch-outs:

3. Bold fit: Font Name or Pairing
   - Use for:
   - Why:
   - Watch-outs:

Implementation:
- Load:
- CSS tokens:
- Body:
- Headings:
- Verification:
```

Use fewer sections when directly editing code, but keep these decisions in mind.

## CSS Implementation Pattern

Use this shape for most projects, adapting names to the existing codebase:

```css
:root {
  --font-sans: "Inter", ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  --font-mono: "Geist Mono", "SFMono-Regular", Consolas, monospace;

  --text-xs: 0.75rem;
  --text-sm: 0.875rem;
  --text-base: 1rem;
  --text-lg: 1.125rem;
  --text-xl: 1.25rem;
  --text-2xl: 1.5rem;
  --text-3xl: 1.875rem;
  --text-4xl: 2.25rem;

  --leading-tight: 1.12;
  --leading-snug: 1.25;
  --leading-normal: 1.5;
  --leading-relaxed: 1.7;
}

html {
  font-family: var(--font-sans);
  font-size: 16px;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
}

body {
  font-size: var(--text-base);
  line-height: var(--leading-normal);
}

h1,
h2,
h3 {
  line-height: var(--leading-tight);
  letter-spacing: -0.02em;
}
```

For Google Fonts, load a constrained family/weight set:

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
```

For self-hosted fonts:

```css
@font-face {
  font-family: "Inter";
  src: url("/fonts/inter-var.woff2") format("woff2");
  font-weight: 100 900;
  font-style: normal;
  font-display: swap;
}
```

## Practical Font Choices

Use the reference file when choosing a font for a particular mood or interface:

- Read [references/font-playbook.md](references/font-playbook.md) when selecting families, pairing fonts, or deciding whether a candidate font is appropriate.
- Read [references/site-type-font-strategy.md](references/site-type-font-strategy.md) when the site category matters, such as banking, finance, healthcare, SaaS, luxury, editorial, portfolio, restaurant, game, or a hero-focused landing page.
- Do not load the full pasted article into context unless the user specifically asks for the original source material.

## Review Checklist

Before finishing typography work, confirm:

- The webpage uses a named custom or intentional system font stack.
- Body text is readable at normal viewing distance.
- Heading and body roles are visually distinct without needing many different fonts.
- Font weights are purposeful: regular for body, medium/semibold for UI emphasis, bold for strong headings.
- Font loading is performant and does not request unused weights.
- Inputs, buttons, tables, nav, captions, and empty states inherit the typography system.
- Fallback fonts are present.
- The design still works if the custom font loads late or fails.
