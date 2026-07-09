# DESIGN.md: Leveraged Strategies Site

---

## 1. Design Philosophy

The site is a methodology reference, not a product landing page. It uses a GitHub Dark-inspired wiki aesthetic: information-dense, developer-credible, calm. Every layout and styling decision prioritizes readability for long-form study. Readers come to understand strategy mechanics in detail, not to skim or be sold to. The visual language is shared with all Azqato properties (teal accent `#00d4a0`, dark surfaces, system fonts, restrained motion) and must not diverge.

---

## 2. Color Palette

All colors are defined as CSS custom properties in `:root` in `css/style.css`. Never hardcode hex values outside this block.

### Base palette

| Token | Hex | Usage |
|-------|-----|-------|
| `--color-bg` | `#0d1117` | Page background |
| `--color-surface` | `#161b22` | Sidebar, cards, table headers |
| `--color-border` | `#30363d` | All borders and dividers |
| `--color-accent` | `#00d4a0` | Links, active nav, h2 bar, hover borders, ticker text, all interactive affordances |
| `--color-accent-hover` | `#00e6b0` | Accent hover state |
| `--color-accent-light` | `rgba(0,212,160,0.08)` | Tinted backgrounds: info callout, table row hover |
| `--color-card-hover` | `#1c2128` | Card and table header hover background |
| `--color-tag-bg` | `#21262d` | Pill backgrounds: badges, ticker tags, hero badge |
| `--color-text-primary` | `#eef3f7` | Body copy, headings, strong text |
| `--color-text-secondary` | `#cbdae6` | Captions, subtitles, nav links (inactive), disclaimers |
| `--color-positive` | `#3fb950` | Gains, favorable metric values |
| `--color-negative` | `#f85149` | Losses, drawdowns, risk-flag text |
| `--color-warning` | `#ffa657` | Caveats, risk callout borders and text |
| `--color-purple` | `#bc8cff` | Reserved; reused as Holy Grail strategy tint |

### Strategy tint palette

Each strategy has one decorative tint used only in its index card top-border (on hover) and its page hero badge dot. Tints are never used for interactive elements. All interactive elements use `--color-accent` exclusively.

| Strategy | Token | Hex | Color name |
|----------|-------|-----|------------|
| 3 Sig | `--color-strat-3sig` | `#79c0ff` | Light blue |
| 6 Sig | `--color-strat-6sig` | `#e3b341` | Amber |
| 9 Sig | `--color-strat-9sig` | `#58a6ff` | Blue |
| TQQQ FTLT | `--color-strat-ftlt` | `#3fb950` | Green (reuses `--color-positive`) |
| Holy Grail | `--color-strat-grail` | `#bc8cff` | Purple (reuses `--color-purple`) |
| HFEA | `--color-strat-hfea` | `#f0883e` | Orange |

### Semantic badge colors

| Badge variant | Background | Text | Border |
|---------------|-----------|------|--------|
| Neutral | `--color-tag-bg` | `--color-text-secondary` | `--color-border` |
| Caution | `rgba(255,166,87,0.12)` | `--color-warning` | `rgba(255,166,87,0.3)` |
| Negative | `rgba(248,81,73,0.12)` | `--color-negative` | `rgba(248,81,73,0.3)` |
| Positive | `rgba(63,185,80,0.12)` | `--color-positive` | `rgba(63,185,80,0.3)` |

---

## 3. Typography

System fonts only. No external font loading. No Google Fonts, no CDN fonts.

```css
/* UI, body, and headings */
-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif

/* Data: tickers, numbers, allocation percentages, code */
'SF Mono', 'Consolas', 'Liberation Mono', 'Courier New', monospace
```

### Type scale

| Role | Element/Class | Size | Weight | Color | Line height | Notes |
|------|--------------|------|--------|-------|-------------|-------|
| Page title | `h1` | 1.875rem | 700 | primary | 1.2 | Letter-spacing -0.3px |
| Section heading | `h2` | 1.375rem | 700 | primary | — | Flex row with teal `::before` bar |
| Subsection | `h3` | 1.0625rem | 600 | primary | — | |
| Body | `p` | 1rem | 400 | primary | 1.6 | |
| Lead / hero sub | `.lead` | 1.0625rem | 400 | primary | 1.65 | |
| Caption / note | `.caption` | 0.78rem | 400 | secondary | — | |
| Logo | `.logo-text` | 1.125rem | 700 | primary | — | Letter-spacing -0.3px |
| Site label | `.site-label` | 0.75rem | 400 | secondary | — | Beneath logo in sidebar |
| Nav link | `.nav-link` | 0.875rem | 500 | secondary | — | Active state: 600 weight, accent color |
| Anchor sub-link | `.anchor-link` | 0.8125rem | 400 | secondary | — | |
| Section label | `.on-this-page-label` | 0.6875rem | 600 | secondary | — | Uppercase, 0.06em tracking |
| Numbers / data | `.num` | 0.85rem | 400 | contextual | — | Monospace |
| Ticker symbol | `.ticker` | 0.875rem | 600 | accent | — | Monospace |
| Table header | `thead th` | 0.6875rem | 600 | secondary | — | Uppercase, 0.06em tracking |
| Table cell | `td` | 0.9rem | 400 | primary | — | |
| Card title | `.card-title` | 1.0625rem | 700 | accent | — | |
| Card summary | `.card-summary` | 0.9rem | 400 | secondary | 1.55 | |
| Footer | `footer` | 0.8rem | 400 | secondary | 1.7 | |

### Mobile type adjustments (max-width: 768px)

| Element | Desktop | Mobile |
|---------|---------|--------|
| `h1` | 1.875rem | 1.5rem |
| `h2` | 1.375rem | 1.2rem |

---

## 4. Spacing System

Base unit: 4px. All spacing uses multiples of 4px. No arbitrary values.

| Value | Common uses |
|-------|-------------|
| 4px | Tight internal gaps (badge padding vertical, `.hero-badge` gap) |
| 6px | Small gaps (hero badge dot-to-label gap) |
| 7px | Nav link vertical padding |
| 8px | Section label bottom padding, sidebar-logo bottom margin |
| 12px | Hero badge horizontal padding, top-bar inner padding vertical |
| 14px | Card footer top padding, hero badge bottom margin, table cell padding |
| 16px | Strategy grid gap, on-this-page top margin/padding, sidebar-nav padding |
| 20px | Sidebar horizontal padding, mobile main padding, top-bar inner horizontal padding |
| 24px | Placeholder padding, sidebar top padding, medium main padding |
| 28px | Desktop main horizontal padding, footer horizontal padding |
| 32px | Desktop main vertical padding, footer vertical padding |

---

## 5. Breakpoints

| Breakpoint | Rule | Effect |
|------------|------|--------|
| `>= 1025px` | (default) | Two-column grid: 220px sidebar + 1fr content. Sidebar visible, top bar hidden. |
| `<= 1024px` | `@media (max-width: 1024px)` | Single-column layout. Sidebar hidden (`display: none`). Top bar shown (`display: block`). Main padding reduces to `24px 20px`. Footer padding reduces to `20px`. Table scrolling enabled. |
| `<= 768px` | `@media (max-width: 768px)` | Strategy cards stack to 1 column. `h1` reduces to 1.5rem, `h2` to 1.2rem. Main padding reduces to `20px`. |

There is no 1440px or 1920px breakpoint. The `max-width: 820px` on `main` contains content naturally at large viewports without additional breakpoints.

---

## 6. Layout

### Grid

```
Desktop (>= 1025px):
  .layout: display grid, grid-template-columns: 220px 1fr
  Sidebar (220px) | Content (flex column, max 820px in main)

Mobile (<= 1024px):
  .layout: grid-template-columns: 1fr
  Sidebar: display none
  Top bar: display block
```

### Sidebar

Fixed at 220px, `position: sticky; top: 0; height: 100vh; overflow-y: auto`. `--color-surface` background, 1px right border in `--color-border`. Contents top to bottom:

1. Logo: "Azqato Invests" (linked to `https://azqato.com/invests`). `logo-text` class with `logo-dot` span for "Invests" in teal.
2. Site label: "Leveraged Strategies" in `--color-text-secondary` at 0.75rem.
3. Nav links: Home, then one link per strategy in nav order, then Individual Stocks (external), ComposerAtlas (external), Support (external). Support is always last.
4. "On This Page" section (strategy pages only): anchor links auto-highlighted on scroll via IntersectionObserver.
5. Footer disclaimer: "Educational use only. Not financial advice." in `--color-text-secondary`.

Active nav link: `--color-accent` text, weight 600, `3px solid --color-accent` left border.

### Top bar (mobile)

`position: sticky; top: 0; z-index: 100`. `rgba(22,27,34,0.9)` background with `backdrop-filter: blur(12px)`. Contains logo (linked) and hamburger button. Nav expands below with `border-top: 1px solid --color-border`. Mobile active state: bottom border instead of left border.

### Content area

`display: flex; flex-direction: column; min-width: 0`. The `min-width: 0` overrides grid/flex item default `min-width: auto`, preventing content from forcing the layout wider than the viewport. Main element: `max-width: 820px; padding: 32px 28px` (desktop), `24px 20px` (1024px), `20px` (768px).

---

## 7. Component Patterns

### Section Heading (h2)

Every h2 carries a `::before` pseudo-element: `display: block; width: 3px; height: 1.1em; background: var(--color-accent); border-radius: 2px`. The h2 uses `display: flex; align-items: center; gap: 0.5rem`. This is the cross-site Azqato signature and appears on all pages. It must not be removed or altered.

### Strategy Cards (index page only)

```
Container: .strategies-grid
  display: grid
  grid-template-columns: repeat(3, 1fr) — collapses to 1fr at 768px
  gap: 16px

Card: .strategy-card
  background: --color-surface
  border: 1px solid --color-border
  border-radius: 10px
  padding: 20px
  position: relative; overflow: hidden
  transition: background 0.15s, transform 0.15s, box-shadow 0.15s

On hover:
  background: --color-card-hover
  transform: translateY(-2px)
  box-shadow: 0 4px 18px rgba(0,212,160,0.07)
  ::before top border: opacity 1 (was 0), color = strategy tint

Card structure:
  .card-body (flex: 1)
    .card-title — 1.0625rem, weight 700, --color-accent
    .card-summary — 0.9rem, --color-text-secondary, line-height 1.55
  .card-footer (border-top: 1px solid --color-border, margin-top 16px, padding-top 14px)
    .card-link — 0.875rem, weight 500, --color-accent
```

### Hero (strategy pages only)

Appears at the top of each strategy page above the first h2.

```
.hero
  margin-bottom: 2rem
  padding-bottom: 2rem
  border-bottom: 1px solid --color-border

.hero-badge — inline-flex pill
  background: --color-tag-bg
  border: 1px solid --color-border
  border-radius: 999px
  padding: 4px 12px
  font-size: 0.75rem
  Contains: .hero-badge-dot (8px circle in strategy tint color) + label text

h1 inside .hero: margin-bottom 12px
.lead inside .hero: color --color-text-primary (not secondary)
```

### Tables

```
Wrapper: .table-wrap
  border: 1px solid --color-border
  border-radius: 8px
  overflow: hidden (clips rounded corners on desktop)
  overflow-x: auto at <= 1024px (enables horizontal scroll on mobile/tablet)
  -webkit-overflow-scrolling: touch at <= 1024px

table
  width: 100%; border-collapse: collapse; font-size: 0.9rem

thead th
  background: --color-card-hover
  font-size: 0.6875rem; weight 600; uppercase; letter-spacing 0.06em
  color: --color-text-secondary; padding: 10px 14px; text-align: left

tbody tr:nth-child(even): rgba(255,255,255,0.02) background
tbody tr:hover: --color-accent-light background
td: padding 10px 14px, color --color-text-primary, border-top 1px --color-border
td.num: text-align right, monospace, 0.85rem
td.positive: --color-positive
td.negative: --color-negative
```

### Callout Boxes

Two variants. Both use `border-radius: 0 6px 6px 0` and `padding: 14px 18px`.

```
.callout-info
  background: --color-accent-light
  border-left: 3px solid --color-accent

.callout-risk
  background: rgba(255,166,87,0.08)
  border-left: 3px solid --color-warning
```

Risk callouts are mandatory on every strategy page. They carry the leveraged ETF risk disclosure covering daily reset, volatility decay, and amplified drawdowns.

### Badges

Pill components with 999px border-radius. Used for metadata labels (rebalancing cadence, risk level, etc.).

```
.badge: display inline-flex; align-items center; border-radius 999px; padding 3px 10px; font-size 0.75rem; weight 500; border: 1px solid

Variants: .badge-neutral, .badge-caution, .badge-negative, .badge-positive
(see Color Palette > Semantic badge colors for exact values)
```

### Ticker Tags

Inline monospace pills for equity tickers (TQQQ, SPY, etc.).

```
.ticker-tag
  display: inline-flex
  font-family: monospace; font-size: 0.8125rem; weight 600
  color: --color-accent
  background: --color-tag-bg
  border: 1px solid --color-border
  border-radius: 6px
  padding: 1px 7px
  transition: background 0.15s, border-color 0.15s

Hover:
  background: --color-accent-light
  border-color: --color-accent
```

The `.ticker` class (inline, no background) is used for tickers within running body text. `.ticker-tag` is used for tickers displayed as standalone interactive chips.

### Inline ticker (body text)

```
.ticker: font-family monospace; font-size 0.875rem; weight 600; color --color-accent
```

### Logo link

The logo is wrapped in `<a class="logo-link">`. The `.logo-link` rule strips all link styling:

```css
a.logo-link {
  text-decoration: none;
  color: inherit;
}
```

This ensures "Azqato Invests" renders identically to before it was a link.

### Skip link

Hidden off-screen by default (`transform: translateY(-100%)`), revealed on focus. Fixed position, top-left corner, teal background, dark text. Required on every page for keyboard accessibility.

### Placeholder blocks (development only)

Used during initial build before real content is ported. Should not appear in production.

```
.placeholder
  border: 1px dashed --color-border
  border-radius: 8px; padding: 24px
  color: --color-text-secondary; font-style italic; text-align center; font-size 0.9rem
```

### Favicon

Emoji SVG data URI, consistent across all pages:

```html
<link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>🚀</text></svg>">
```

---

## 8. Accessibility Standards

Target: WCAG 2.1 Level AA.

- **Contrast:** `--color-text-primary` (`#eef3f7`) on `--color-bg` (`#0d1117`) is approximately 15:1. `--color-text-secondary` (`#cbdae6`) on `--color-bg` is approximately 4.8:1. Both exceed AA (4.5:1 for normal text).
- **Focus indicators:** All interactive elements show a 2px `--color-accent` outline with 3px offset on `:focus-visible`. The `focus-visible` pseudo-class limits outlines to keyboard navigation, avoiding outline clutter for mouse users.
- **Skip link:** Every page begins with `<a class="skip-link" href="#main-content">Skip to content</a>` as the first focusable element.
- **Tables:** Use `<th scope="col">` on all column headers. Tables with non-obvious content include visually hidden `<caption>` elements using `.visually-hidden`.
- **ARIA:** `aria-label` on `<nav>` elements to distinguish sidebar from top-bar nav. `aria-current="page"` on the active nav link. `aria-expanded` and `aria-controls` on the mobile nav toggle. `role="note"` and `aria-label` on risk callout divs. `aria-hidden="true"` on decorative SVG icons.
- **Strategy tints:** Never used as the sole differentiator. Cards and badges always carry text labels alongside tint color.
- **Reduced motion:** `@media (prefers-reduced-motion: reduce)` disables card hover transitions and skip-link transition. `scroll-behavior` reverts to `auto`.
- **Semantic HTML:** Strategy sections use `<article>` for cards, `<aside>` for sidebar, `<main>` for content, `<nav>` for navigation, `<footer>` for footer.

---

## 9. Animation and Motion

Motion is minimal and purposeful. No animations exist for decoration.

| Element | Motion | Duration | Easing |
|---------|--------|----------|--------|
| Strategy card hover | `translateY(-2px)` + background change | 150ms | default (ease) |
| Strategy card `::before` top border | opacity 0 to 1 | 150ms | default |
| Nav link, anchor link color | color transition | 150ms | default |
| Skip link reveal | `translateY(-100%)` to `0` | 150ms | default |
| Ticker tag hover | background + border-color | 150ms | default |

All transitions are disabled by `@media (prefers-reduced-motion: reduce)`.

No loading animations, no scroll animations (IntersectionObserver only changes classes, not positions), no animated page transitions.

---

## 10. What Not To Do

- No light backgrounds or light theme. Dark only.
- No external fonts, CDNs, icon libraries, or JavaScript frameworks.
- No live data, charts, widgets, or price embeds.
- No gradients except the strategy tint top border on card hover.
- No motion beyond the transitions listed in the Animation section.
- No em dashes (U+2014 literal or `&mdash;` entity) in any copy. Use a comma, colon, semicolon, parentheses, or period as appropriate.
- Never use a strategy tint color for interactive elements. `--color-accent` (`#00d4a0`) is the only interactive accent color.
- No marketing language, urgency cues, countdowns, or calls to action.
- No real-time data references. All content must read accurately regardless of current market conditions.

---

## 11. Navigation Convention

Every `.md` file added to `/strategies` implies a new page, a new nav entry in every existing page, and a new strategy card on `index.html`. When adding a strategy:

1. Add nav `<li>` in alphabetical or logical order after existing strategy links
2. Add before the Individual Stocks link
3. Support is always the last nav item; never replace it or push it further down

---

## 12. Content Philosophy

- No real-time data. Nothing that goes stale within weeks (current prices, live allocation percentages, fund NAV).
- Historical references must clearly read as past events.
- Performance discussion describes behavior and character (drawdown depth, recovery patterns) rather than predictions.
- Every strategy page carries a mandatory risk callout covering leveraged ETF mechanics: daily reset, volatility decay, amplified drawdowns.
- Attribution: credit original strategy authors and sources in the Resources section of each strategy page.

---

## 13. CSS File Structure

The order of rules in `css/style.css` must be maintained. Do not reorganize.

```
:root — Design tokens (all custom properties)
Reset / base (*, html, body, a, ul, img)
Layout grid (sidebar + content)
Sidebar and top-bar nav
Typography (h1, h2 with ::before bar, h3, body, lead, captions, ticker)
Hero (badge, title, sub)
Strategy cards (index page)
Placeholder blocks
Tables
Callout boxes (info, risk)
Badges and ticker tags
Footer
Media queries (@media max-width: 1024px, then 768px)
Reduced motion
```

---

## 14. JavaScript

`js/main.js` contains two behaviors only:

1. **IntersectionObserver anchor highlighting:** On strategy pages, watches the five section elements (`#overview`, `#rules`, `#performance`, `#risks`, `#resources`) and adds `.is-active` to the matching `.anchor-link` in the sidebar as sections enter the viewport. Uses `rootMargin: '-15% 0px -80% 0px'` to trigger when a section is approximately one-fifth down from the top of the viewport.

2. **Mobile nav toggle:** Listens for clicks on `.nav-toggle`, toggles `aria-expanded` between true/false, and toggles the `hidden` attribute on `#mobile-nav`.

Both behaviors are progressive enhancements. The site is fully usable with JavaScript disabled.

---

## 15. AI Context

For AI models working on this codebase:

- The entire design system lives in one file: `css/style.css`. Read it in full before making style changes.
- All custom properties (`--color-*`, `--font-*`) must be used. Never hardcode hex values.
- The `--color-accent` (`#00d4a0`) is a cross-site brand constant. Do not change it.
- The h2 `::before` accent bar is a brand signature. Do not remove it.
- The `min-width: 0` on `.content-wrap` is intentional and must not be removed. It prevents grid item overflow.
- `overflow-x: auto` on `.table-wrap` applies at `<= 1024px`, not just `<= 768px`. This is intentional to cover the 769px to 1023px gap where single-column layout is active but table content could overflow.
- Strategy tint colors (`.strat-*::before`) only appear on hover on index cards and as the dot in hero badges on strategy pages. They must never appear on links, buttons, or any interactive element.
- The `.logo-link` rule (`text-decoration: none; color: inherit`) is what prevents the logo from appearing as a blue underlined link. Do not remove it.
- Every strategy page must include the risk callout (`.callout-risk`) as the first piece of content in the Risks and Caveats section.
