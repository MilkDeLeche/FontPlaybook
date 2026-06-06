# Font Playbook

Use this reference when selecting and applying webpage fonts.

## Display vs Text

Display type is for large headings, hero copy, posters, pull quotes, and brand moments. It can be tighter, more distinctive, and more emotional.

Text type is for paragraphs, UI labels, menus, form controls, captions, tables, and anything read at small sizes. It must prioritize legibility and rhythm over personality.

Many modern families work for both roles. When using one family for both, create distinction with size, weight, line-height, and modest heading letter-spacing.

## Selection Heuristics

Prefer a font that has:

- At least five weights, such as regular, medium, semibold, bold, and black or light.
- Italics when the content needs editorial emphasis.
- Good punctuation, symbols, currency, arrows, math marks, and UI glyphs.
- Required language support.
- Clear `0/O`, `1/l/I`, and readable numerals for data-heavy UIs.
- A high enough x-height for small labels and dense screens.
- A variable font file when performance and flexible weights matter.

Avoid:

- Trendy novelty faces for body text.
- Thin weights for important UI text.
- All-caps navigation with wide tracking unless it fits the brand and remains readable.
- Loading every font weight from a hosted provider.
- Pairing fonts just to make the design feel more designed.

## Strong Free UI Fonts

Neutral, highly usable defaults:

- Inter: excellent all-purpose UI and body font; strong default for SaaS and product work.
- Public Sans: sober, government/design-system feel; good for forms and information systems.
- Source Sans 3 / Source Sans Pro: readable, familiar, editorial-friendly UI sans.
- IBM Plex Sans: institutional, technical, and trustworthy; good for finance, enterprise, and data-heavy products.
- Open Sans: extremely readable and mature, but can feel common.
- Work Sans: approachable, practical, and readable.

Modern product and developer feel:

- Geist Sans: crisp, technical, minimal, good for developer tools and modern product UIs.
- Mona Sans: versatile GitHub-designed sans with width/weight flexibility.
- Hubot Sans: more distinctive, best for headings, technical branding, or accents.
- Space Grotesk: distinctive grotesk; good for headings and modern brand surfaces.
- Manrope: modern and slightly condensed; useful for numeric/data-heavy interfaces.

Friendly geometric or casual:

- Figtree: clean but warm; good balance for approachable products.
- DM Sans: low-contrast and strong at small sizes.
- Outfit: simple geometric personality, strong for landing pages and brand-forward UI.
- Poppins: geometric and broad language support; use carefully because it is common.
- General Sans: compact, friendly, useful for mobile and dense UI.

Accessibility and multilingual emphasis:

- Lexend: designed for readability and accessibility-sensitive contexts.
- Hind: humanist and screen-oriented.
- Be Vietnam Pro: strong Vietnamese support and clean UI styling.
- Fira Sans: broad, readable, mature.

Premium or license-dependent inspirations:

- Neue Haas Grotesk: classic neutral grotesk.
- Aktiv Grotesk: authoritative, modern grotesk.
- Futura PT: geometric, brand-forward, less ideal for dense body UI.
- Sohne: premium modern grotesk often seen in polished product/brand work.

## Pairing Patterns

Use one family:

- Best for product UI, dashboards, admin tools, and most apps.
- Create hierarchy with weight, size, spacing, and color.

Use sans plus expressive display:

- Best for marketing, portfolio, editorial, or brand pages.
- Keep the display face mostly to H1/H2 and large callouts.
- Keep body and UI controls in a readable sans.

Use sans plus mono:

- Best for developer tools, technical docs, pricing calculators, data labels, and code.
- Mono should be used sparingly for code, tokens, IDs, metrics, or keyboard commands.

## CSS Loading Guidance

Hosted Google Fonts:

- Preconnect to `fonts.googleapis.com` and `fonts.gstatic.com`.
- Use `display=swap`.
- Request only used weights and styles.
- Prefer variable font axes when the provider supports them and the project uses many weights.

Self-hosted fonts:

- Use `woff2`.
- Put font files in a predictable public asset path.
- Declare `font-display: swap`.
- Declare exact weight ranges for variable fonts.
- Keep fallback metrics acceptable; test the page while throttled or after disabling the custom font.

System stack:

- Use when performance, privacy, or native platform feel matters more than custom brand expression.
- A good sans stack is `ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif`.

## Type Scale Starting Points

For product UI:

```css
--text-xs: 0.75rem;
--text-sm: 0.875rem;
--text-base: 1rem;
--text-lg: 1.125rem;
--text-xl: 1.25rem;
--text-2xl: 1.5rem;
--text-3xl: 1.875rem;
```

For marketing/editorial pages:

```css
--text-sm: 0.875rem;
--text-base: 1rem;
--text-lg: 1.125rem;
--text-xl: 1.25rem;
--text-2xl: 1.5rem;
--text-3xl: 2rem;
--text-4xl: 2.5rem;
--text-5xl: 3rem;
```

Set larger sizes with breakpoints or component variants. Avoid tying font size directly to viewport width unless carefully bounded.

## Line Height and Tracking

Body text:

- Start at `line-height: 1.5`.
- Use `1.6` to `1.75` for long paragraphs.
- Use `1.35` to `1.5` for compact UI labels and lists.

Headings:

- Start at `line-height: 1.1`.
- Use `1.0` to `1.15` for large hero headings.
- Use `1.2` to `1.3` for smaller section headings.

Letter-spacing:

- Body text usually stays at `0`.
- Large headings may use `-0.01em` to `-0.04em`.
- Small uppercase labels may use `0.04em` to `0.08em`, but only when the text remains readable.

## Common Fixes

If the page feels generic:

- Replace browser/system defaults with one deliberate family.
- Increase heading weight contrast, not font count.
- Tune line-height and paragraph measure.
- Use medium/semibold for UI emphasis instead of bold everywhere.

If the page feels cluttered:

- Reduce the number of font families.
- Reduce the number of type sizes.
- Normalize weights.
- Increase line-height and section spacing before changing fonts.

If text is hard to read:

- Raise body size to at least `16px`.
- Increase line-height.
- Pick a font with better x-height and clearer counters.
- Avoid light weights and low-contrast text colors.

If performance is poor:

- Remove unused font weights.
- Prefer one variable `woff2` file.
- Self-host when appropriate.
- Use system fonts for dense internal tooling when custom typography is not important.
