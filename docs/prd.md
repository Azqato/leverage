# PRD.md: Leveraged Strategies Site

---

## 1. Problem Statement

Information about leveraged ETF strategies is scattered across forum threads, paywalled newsletters, YouTube videos, and community backtesting tools with inconsistent methodology. There is no single, clean, readable reference that documents the well-known leveraged ETF strategy frameworks side by side in a consistent format. Investors who want to understand the mechanics of 9 Sig, TQQQ FTLT, HFEA, or the other major frameworks must piece together information from many sources of varying quality, often encountering marketing language, incomplete rules, or outright errors (as documented in the BestFolio corrected backtest, which identified five implementation errors common in community tools).

This site solves that by providing one authoritative, hype-free, mechanics-first reference covering six strategies with a consistent structure.

---

## 2. Target Users

**Primary: Self-directed leveraged ETF investor (research mode)**
Someone who already knows what TQQQ is, has decided to explore leveraged ETF strategies, and wants to understand the actual mechanics before committing capital. They read long-form material carefully. They are skeptical of hype and value clear attribution to original sources. They will spend 20 to 60 minutes reading a strategy page.

**Secondary: Newer investor doing due diligence**
Someone who has heard of HFEA or 9 Sig from a community forum and wants an honest explanation including the risks. They may not understand leveraged ETF mechanics yet. The site's risk callouts and conservative framing serve this persona without the site being condescending to the primary user.

**Tertiary: AI model or developer working on the codebase**
A person or AI instance reading the docs folder to understand the project before making changes. The `/docs` folder, combined with the `/strategies/*.md` source files, should be sufficient to understand the entire project without reading code.

---

## 3. Goals

1. Document six strategies (3 Sig, 6 Sig, 9 Sig, TQQQ For The Long Term, Holy Grail, HFEA) in a consistent, readable format
2. Ship a working multi-page static site with no external dependencies that deploys to GitHub Pages with zero configuration
3. Maintain visual and structural consistency with other Azqato properties
4. Provide content that remains accurate over time without requiring updates tied to market conditions
5. Serve as the canonical reference for these strategies within the Azqato site family

---

## 4. Non-Goals

- No live market data, charts, or price feeds
- No backtesting tools or calculators
- No user accounts, comments, or community features
- No recommendations or signals. The site documents methodologies; it does not tell anyone what to buy or sell
- No mobile app or native experience
- No server-side rendering or database
- No email capture or newsletter

---

## 5. User Stories

**As a self-directed investor,** I want to read a complete explanation of the 9 Sig strategy mechanics so that I understand exactly what the plan requires me to do each quarter before I commit capital.

**As a self-directed investor,** I want to see the historical performance data and drawdown figures for each strategy so that I can calibrate my risk tolerance against what has actually happened historically.

**As a new investor,** I want to understand the risks specific to leveraged ETFs before reading strategy details so that I am not surprised by the risk profile after already forming a positive impression.

**As an investor comparing strategies,** I want each strategy page to have the same five-section structure so that I can compare equivalent sections across strategies without hunting for information.

**As a keyboard-only user,** I want to navigate the full site using only the keyboard so that the site is accessible regardless of how I use my computer.

**As a mobile user,** I want to read strategy pages on my phone without needing to scroll horizontally so that the experience is usable on a small screen.

**As a contributor or AI model,** I want the `/docs` folder to contain enough information to understand the entire project so that I can make changes confidently without reverse-engineering the codebase.

---

## 6. Feature List

### MVP (shipped)

- Seven HTML pages: one home page and one dedicated page per strategy
- Consistent five-section structure on all strategy pages (Overview, Rules and Logic, Performance Notes, Risks and Caveats, Resources)
- Persistent wiki-style sidebar navigation on desktop (>= 1025px) with active page highlight and scroll-based section highlighting
- Sticky blurred top bar on mobile (<= 1024px) with hamburger-toggle navigation
- Strategy cards on the home page with strategy-specific tint colors
- Mandatory leveraged ETF risk callout on every strategy page
- Full strategy content for all six strategies, ported from `/strategies/*.md` source files
- Cross-site navigation links to Individual Stocks and ComposerAtlas (other Azqato properties)
- Linked logo ("Azqato Invests") in header pointing to `https://azqato.com/invests`
- GitHub Pages deployment with no build step required
- WCAG 2.1 AA accessibility (skip link, focus indicators, semantic HTML, ARIA attributes)

### Future (post-launch, not yet scheduled)

- Strategy comparison page: all six strategies side by side in a structured table
- Glossary page: leveraged ETF terms (volatility decay, daily reset, beta slippage, value averaging)
- Calculator or signal tracker for the Kelly Signal plans
- Client-side rendering of `/strategies/*.md` markdown content (eliminates manual HTML porting step)
- Search functionality across all strategy content
- Printer-friendly or PDF export per strategy page
- Dark/light theme toggle (currently dark only)

---

## 7. Constraints

- No Node.js, no npm, no build tools. Deployment must work by pushing HTML/CSS/JS files to a git repository.
- No external dependencies of any kind: no CDN fonts, no icon libraries, no CSS frameworks, no JavaScript libraries.
- GitHub Pages hosting only. No server-side code, no dynamic routing, no database.
- Content must be accurate over time without market-condition updates. No live prices, no dated "as of" figures for current conditions.
- Dark theme only. The Azqato brand system does not include a light theme for this property.

---

## 8. Assumptions

- Visitors arrive with at least basic knowledge of ETFs. The site does not explain what an ETF is.
- All strategies documented are educational references, not recommendations. Legal risk is managed by the disclaimer on every page, not by gatekeeping content.
- The `/strategies/*.md` content source files are the authoritative source for strategy facts. HTML pages are derived from them and must be updated when `.md` files are corrected.
- GitHub Pages will remain free and available for this project.
- The Azqato brand system (`#00d4a0` accent, dark palette, system fonts) is stable and will not change.

---

## 9. Success Criteria

- Site is live at `https://azqato.github.io/leverage/` with all seven pages navigable
- All six strategy pages share the same five-section skeleton
- Lighthouse accessibility score of 95 or higher on every page
- Total page weight under 100KB per page (no images required)
- Strategy content can be updated by editing one HTML file per strategy without touching layout code
- The site reads correctly with JavaScript disabled
- No horizontal overflow at any viewport width from 375px to 1920px

---

## 10. Tenets

Ordered by priority. When two tenets conflict, the higher-ranked tenet wins.

**1. Accuracy over completeness.** A gap in coverage is preferable to inaccurate information. If a strategy rule cannot be confirmed from a primary source, leave the section blank or flag it explicitly. Do not fill gaps with inference presented as fact.

**2. Mechanics first, performance second.** Every strategy page must explain how the strategy works before it discusses what returns it has produced. A reader who understands the mechanics can evaluate the performance data critically. A reader who sees performance first cannot.

**3. No dark patterns.** The site does not use urgency, social proof, loss aversion framing, or other persuasion techniques borrowed from marketing. It describes strategies neutrally. If a strategy has serious risks, those risks are stated clearly and not buried.

**4. Stable over current.** Content that remains accurate for years is more valuable than content that is accurate today. Do not include data points that will be outdated within months (current price levels, last week's signal values, current allocations). Reference historical events and verified backtest figures instead.

**5. One canonical source.** Each strategy has one content source file (`/strategies/<name>.md`). The HTML page is derived from it. When facts change, they change in the `.md` file first. This single-source discipline prevents drift between the research document and the public page.

**6. Simple over clever.** The site is vanilla HTML, CSS, and JavaScript. The technology choice is a constraint enforced by this tenet: if a feature requires a build step, a library, or a server, it does not ship. Simplicity is not a compromise; it is a requirement for long-term maintainability.

**7. Reader orientation over design expression.** Layout decisions serve the reader's ability to find and understand information. The persistent sidebar, in-page anchor links, consistent section structure, and five-section template all exist to keep readers oriented in long documents. Decorative design choices that impair orientation are not made.

---

## 11. Roadmap

### Current phase: Post-launch polish (v1.x)

The site launched as v1.0.0 in June 2026 with full content for all six strategies. The current phase focuses on documentation quality, code correctness, and cross-site integration. No new strategies are planned.

### Milestone table

| Milestone | Version | Target | Status | Description |
|-----------|---------|--------|--------|-------------|
| Skeleton build | v0.1.0 | June 2026 | Complete | Seven pages, shared nav, placeholder strategy sections |
| Content drafts | v0.1.x | June 2026 | Complete | All six `/strategies/*.md` files researched and fully written |
| Content port | v1.0.0 | June 2026 | Complete | All placeholders replaced with real content; four badge/lead corrections applied; site launched |
| Docs and launch | v1.0.1 | June 2026 | Complete | Docs sync; GitHub Pages deployment; live URL confirmed |
| Post-launch polish | v1.1.0 | July 2026 | Complete | Documentation audit; em dash cleanup; mobile CSS bug fix |
| Comparison page | v2.0.0 | TBD | Planned | All-six-strategy side-by-side comparison table |
| Glossary | v2.1.0 | TBD | Planned | Leveraged ETF term definitions page |

### Explicitly deferred

- **Calculator/signal tracker:** Requires JavaScript logic for strategy signal calculations. Deferred because it requires ongoing accuracy maintenance as strategy parameters change, which conflicts with the "stable over current" tenet.
- **Live data feeds:** Permanently deferred. Violates the "stable over current" tenet and requires server infrastructure.
- **Client-side markdown rendering:** Would eliminate the manual HTML porting step. Deferred because it requires a JavaScript markdown parser (external dependency) and changes the rendering model. The current manual porting approach is low-frequency and well-understood.
- **Light theme:** Deferred indefinitely. The Azqato brand system is dark-only for this property.

---

### Session handoff note: 2026-07-08

The v1.1.0 work was started in a single long session and paused before completion due to context limits. This note documents exactly what was done and what remains so the next session can pick up cleanly.

#### What was completed in this session

**Documentation rewrites (all 4 files):**
- `README.md`: complete rewrite, developer-focused, no marketing language
- `docs/PRD.md`: complete rewrite with all required sections (this file)
- `docs/DESIGN.md`: complete rewrite with Spacing System, Component Patterns, Accessibility, AI Context sections
- `docs/PATCHNOTES.md`: converted from milestone versioning to semver; all history preserved

**Em dash cleanup in HTML pages (all 7 files, verified clean):**
- `index.html`: 1 replacement
- `3sig.html`: ~10 replacements (title, signal line, 30 Down Rule, COVID crash, closed-system, risk callout, BestFolio h3, resource list)
- `6sig.html`: ~8 replacements (title, mechanics pair, MVV appositive, BestFolio h3, bond buffer, resource list)
- `9sig.html`: ~12 replacements (title, safeguards, TQQQ appositive, core mechanics pair, ratio drift, 30 Down, BestFolio h3, internal quote, risk callout x2, resource list)
- `tqqq-ftlt.html`: ~10 replacements (title, meta, SMA pair, October 2022, live performance dash, Step 1, backtest window, Great Depression, risk callout, resource list)
- `hfea.html`: 4 replacements (title, regime-adaptive h3, TMV appositive, bond decline)
- `holy-grail.html`: ~9 replacements (title, meta, event-driven, 200D SMA, bull regime, Step 1, SOXL, academic h3, resource list)
- Final grep confirmed: zero em dashes remaining in any `.html` file

**CSS mobile fix:**
- `css/style.css`: added `overflow-x: auto; -webkit-overflow-scrolling: touch;` to the `@media (max-width: 1024px)` block so tables scroll at 769px-1023px (previously broken, only worked at 768px and below)

**Patchnotes em dash cleanup:**
- `docs/PATCHNOTES.md`: rewritten in full; all heading separators changed from `## [vX.Y.Z] — YYYY-MM-DD — title` to `## [vX.Y.Z] YYYY-MM-DD: title`; all bullet `` `file` — description `` changed to `` `file`: description ``

#### What remains to complete the original prompt

**1. Em dash cleanup in docs (minor, ~5 minutes):**
- `docs/prd.md` line 458: the RESEARCH SOURCES comment example uses ` — `; change to `: ` to match the Writing Style rule
- `docs/prd.md` line 503: the Press Release dateline `**ONLINE, June 2026** — Azqato today launched` should change to `**ONLINE, June 2026:** Azqato today launched`
- `docs/design.md` code blocks: em dashes appear inside fenced code blocks as pseudocode notation (e.g., `.card-title — 1.0625rem`). Decision pending: treat code fences as exempt from the prose rule (recommended) or replace with colons.
- `strategies/*.md` source files: contain em dashes in prose. These are not published HTML but the Writing Style section says they should follow the same rules. Decision pending: fix or leave.

**2. GitHub Wiki setup (~15-30 minutes):**
Run: `git clone https://github.com/Azqato/leverage.wiki.git` in a temp directory (PowerShell, outside the repo).
- If it fails (no wiki exists yet): tell user to go to `https://github.com/Azqato/leverage` > Settings > Features > enable Wikis, then create one placeholder page (any title). Then re-run the clone.
- If it succeeds: diff the existing wiki pages against `docs/PRD.md`, `docs/DESIGN.md`, `docs/PATCHNOTES.md`, and `README.md`. Build or update these wiki pages: `Home.md`, `Product-Overview.md`, `Patch-Notes.md`, plus a `_Sidebar.md` for navigation. Push the wiki repo.

**3. Final git commit and push (user must approve first):**
- Stage all changed files: `index.html`, `3sig.html`, `6sig.html`, `9sig.html`, `tqqq-ftlt.html`, `hfea.html`, `holy-grail.html`, `css/style.css`, `README.md`, `docs/PRD.md`, `docs/DESIGN.md`, `docs/PATCHNOTES.md`
- Commit message: `v1.1.0 — docs audit, em dash cleanup, mobile CSS fix`
- Present the complete list of changed files to user and wait for approval before running `git push origin main`

#### Pending decision from user

Before the next session continues, the user needs to answer:
1. Should em dashes inside fenced code blocks in `docs/DESIGN.md` be replaced (they are pseudocode spec notation, not prose)?
2. Should `strategies/*.md` source files have their em dashes cleaned up, or are they out of scope?

---

## 12. Metrics

**North star metric:** Time on page for strategy pages. A reader who finishes a strategy page has extracted value from the site.

**Acquisition metrics**
- Unique visitors per month
- Traffic source breakdown (organic search, direct, referral, social)
- Search impressions and clicks (Google Search Console)
- Target: 500 unique visitors per month within 6 months of launch

**Engagement metrics**
- Average time on page per strategy (target: 4 minutes or more, indicating full read)
- Bounce rate per strategy page (target: under 60%)
- Pages per session (target: 1.8 or higher, indicating cross-strategy browsing)

**Retention metrics**
- Returning visitor percentage (target: 15% or more)
- Not a priority for a reference site; return visits indicate reference usage, not engagement failure

**Performance metrics**
- Lighthouse Performance score: target 95 or higher
- Lighthouse Accessibility score: target 95 or higher
- First Contentful Paint: target under 1 second
- Total page weight: target under 100KB per page
- No 404 errors on live pages

**Measurement method**
- GitHub Pages does not provide built-in analytics. Measurement requires adding a privacy-respecting analytics tool (Plausible, Fathom, or Google Analytics) or monitoring via Google Search Console.
- Lighthouse audits run manually or via CI before major releases.

**Reporting cadence**
- Performance audits: before each major version release
- Traffic metrics: monthly review if analytics are added

---

## 13. Runbook

### Local setup

Requirements: Git, a modern web browser, Python 3 (optional but recommended).

```bash
git clone https://github.com/Azqato/leverage.git
cd leverage
python3 -m http.server 8000
```

Open `http://localhost:8000`. No other setup required.

To open without a local server: open `index.html` directly in a browser. Most features work, but some browsers log MIME-type warnings for CSS/JS loaded from `file://` URLs.

### Build

There is no build step. The repository is the deployable artifact.

### Deploy

**Production deployment (GitHub Pages):**

```bash
git add <files>
git commit -m "describe the change"
git push origin main
```

GitHub Pages is configured to serve from the `main` branch, repo root. Changes go live within 1 to 3 minutes of the push completing. The live URL is `https://azqato.github.io/leverage/`.

No CI/CD pipeline exists. Deployment is manual push to `main`.

**Staging:** There is no staging environment. Test locally before pushing to `main`.

### Rollback

Option A: revert a specific commit.

```bash
git revert <commit-hash>
git push origin main
```

Option B: hard reset to a known-good commit (destructive; confirm before using).

```bash
git log --oneline          # find the target hash
git reset --hard <hash>
git push --force origin main
```

GitHub Pages will redeploy on the next push. There is no cache to invalidate manually; GitHub Pages CDN propagation takes a few minutes.

### Environment configs

There is only one environment: production (GitHub Pages). There are no environment variables, no `.env` files, and no config differences between local development and production. What you run locally is exactly what ships.

### Common errors

| Error | Likely cause | Fix |
|-------|-------------|-----|
| CSS not loading when opening `index.html` directly | Browser blocking `file://` CSS imports | Use `python3 -m http.server 8000` instead |
| Push rejected | Branch protection or wrong remote | Check `git remote -v`; confirm remote is `https://github.com/Azqato/leverage` |
| Site not updating after push | GitHub Pages propagation delay | Wait 2 to 5 minutes; hard refresh the browser (`Ctrl+Shift+R`) |
| Strategy page shows placeholder content | HTML page not updated after `.md` edit | Port the updated content from the `.md` file to the HTML manually |
| Nav link missing on one page | Forgot to add `<li>` to all 7 pages | Check all 7 HTML files; both sidebar and top-bar nav blocks on each |

### Monitoring

There is no uptime monitoring. GitHub Pages has historically high availability. To check if the site is up: visit `https://azqato.github.io/leverage/` directly.

Error monitoring: none automated. Errors surface through manual testing.

---

## 14. Technical Requirements

### System architecture

Fully static site. Client renders HTML, CSS, and JavaScript files served by GitHub Pages CDN. No server-side logic, no API calls, no database. The architecture has zero moving parts: push to git, files served over HTTPS.

### Tech stack

| Layer | Technology | Version | Purpose |
|-------|-----------|---------|---------|
| Markup | HTML5 | — | Page structure and content |
| Styles | CSS3 | — | Design system, layout, responsive behavior |
| Scripts | JavaScript (ES5-compatible IIFE) | — | Scroll highlighting, mobile nav toggle |
| Hosting | GitHub Pages | — | Static file hosting from `main` branch root |
| Version control | Git | — | Source control and deployment trigger |

No Node.js, no npm, no webpack, no Babel, no TypeScript, no CSS preprocessor, no framework.

### Folder structure

```
/
├── index.html              Home page
├── 3sig.html               3 Sig strategy
├── 6sig.html               6 Sig strategy
├── 9sig.html               9 Sig strategy
├── tqqq-ftlt.html          TQQQ For The Long Term strategy
├── holy-grail.html         Holy Grail strategy
├── hfea.html               HFEA strategy
├── css/
│   └── style.css           All design tokens, reset, layout, and component styles
├── js/
│   └── main.js             IntersectionObserver anchor highlighting; mobile nav toggle
├── strategies/
│   ├── 3sig.md             Research and content source for 3sig.html
│   ├── 6sig.md             Research and content source for 6sig.html
│   ├── 9sig.md             Research and content source for 9sig.html
│   ├── tqqq-ftlt.md        Research and content source for tqqq-ftlt.html
│   ├── holy-grail.md       Research and content source for holy-grail.html
│   └── hfea.md             Research and content source for hfea.html
└── docs/
    ├── PRD.md              This file
    ├── DESIGN.md           Design system specification
    └── PATCHNOTES.md       Changelog
```

### Data models

This site has no data models in the traditional sense. The primary content unit is the strategy, represented as:

**Strategy (static, compile-time)**
- `name` (string): display name (e.g., "9 Sig", "HFEA")
- `slug` (string): filename-safe identifier (e.g., "9sig", "hfea")
- `htmlFile` (string): page file path (e.g., "9sig.html")
- `sourceFile` (string): content source path (e.g., "strategies/9sig.md")
- `tintToken` (string): CSS custom property (e.g., "--color-strat-9sig")
- `navLabel` (string): text in the navigation list
- `badge` (string): hero badge label (e.g., "Quarterly Rebalancing")
- `sections` (array): five sections (Overview, Rules and Logic, Performance Notes, Risks and Caveats, Resources)

All of the above is static and hardcoded in HTML. There is no runtime data fetching.

### API design

This site makes no API calls. There is no internal data flow beyond DOM manipulation in `main.js`. The two JavaScript behaviors:

**IntersectionObserver (scroll highlighting)**
- Input: presence of `.anchor-link` elements in the DOM
- Behavior: watches `#overview`, `#rules`, `#performance`, `#risks`, `#resources` section elements; adds `.is-active` to the matching `.anchor-link` when the section enters the viewport at `-15% 0px -80% 0px` root margin
- Output: `.is-active` class on zero or one `.anchor-link` at a time
- Error states: if no `.anchor-link` elements exist (home page), does nothing

**Mobile nav toggle**
- Input: click on `.nav-toggle` button
- Behavior: toggles `aria-expanded` attribute between "true" and "false"; toggles `hidden` attribute on `#mobile-nav`
- Output: nav shown or hidden
- Error states: if `.nav-toggle` or `#mobile-nav` is not in the DOM, does nothing

### State management

No application state. The only dynamic state is:
- `.is-active` class on sidebar anchor links (ephemeral, set by IntersectionObserver)
- `aria-expanded` attribute on mobile nav toggle (ephemeral, toggled by click)
- `hidden` attribute on `#mobile-nav` (ephemeral, toggled by click)

No localStorage, no cookies, no session state.

### Third-party integrations

| Service | Purpose | Data sent | Authentication |
|---------|---------|-----------|----------------|
| GitHub Pages | Static file hosting and CDN | None (serves files only) | GitHub account for push access |
| `azqato.com/invests` | Logo link destination | None (outbound link only) | None |
| `azqato.github.io/stocks/` | Cross-site nav link | None (outbound link only) | None |
| `azqato.github.io/composer/` | Cross-site nav link | None (outbound link only) | None |
| `azqato.github.io/support.html` | Support nav link | None (outbound link only) | None |

No analytics, no tracking pixels, no third-party scripts of any kind.

### Performance requirements

- First Contentful Paint: under 1 second on a fast connection
- Total page weight: under 100KB per page (no images; CSS approximately 20KB, HTML approximately 30 to 60KB depending on strategy length, JS approximately 2KB)
- No render-blocking resources: CSS in `<head>`, JS at end of `<body>`
- No layout shift: no fonts loading asynchronously, no images without dimensions

### Known technical debt

- **Manual HTML porting:** When `/strategies/*.md` content is updated, the corresponding HTML page must be manually edited. This creates a drift risk. The correct solution is client-side markdown rendering or a static site generator, both deferred for dependency reasons.
- **Nav duplication:** Each of the 7 HTML pages contains identical nav markup (14 `<li>` elements across sidebar and top-bar nav). Adding or changing a nav item requires editing all 7 files. The correct solution is a templating system or SSG, deferred for the same reason.
- **Indentation inconsistency in index.html sidebar:** The Individual Stocks and ComposerAtlas `<li>` elements in `index.html` sidebar use 8-space indentation while surrounding items use 10-space indentation. Cosmetic only; no functional impact.

---

## 15. Security

### Authentication model

There are no users. There is no authentication. The site is fully public with no login, no session management, and no private content.

### Authorization model

Not applicable. All content is public. The only privileged action is pushing to the `main` branch on GitHub, which is controlled by GitHub account access.

### Data storage

No user data is stored anywhere. The site does not set cookies, does not use localStorage, does not use sessionStorage, and makes no API calls that could transmit user data.

### Environment variables

There are no environment variables. There are no secrets. There is nothing to protect in a `.env` file and none should be created.

### Third-party trust

| Service | Data received from users | Notes |
|---------|------------------------|-------|
| GitHub Pages | IP address (standard CDN logging) | GitHub Privacy Policy governs |
| All outbound links | Nothing until user clicks | Standard browser navigation; no tracking |

No analytics, no advertising pixels, no chat widgets, no form submissions. The site cannot leak user data because it collects none.

### Known attack surface

- **Outbound links only:** All external links open in the same tab by default (no `target="_blank"` without `rel="noopener"`). Check any new external links for correct `rel` attributes.
- **No forms:** No user input is accepted. XSS and injection are not applicable.
- **No dynamic content:** All HTML is static. There is no server-side rendering where injection could occur.
- **Content security:** No inline JavaScript (except the emoji favicon SVG data URI, which is not executable). The single external script (`js/main.js`) is served from the same origin.

### Dependency policy

There are no dependencies to monitor. If a dependency is ever added (e.g., an analytics library), it must be:
1. Self-hosted or served from the same origin
2. Reviewed for what data it collects before adding
3. Documented in this section

---

## 16. Content Management

### Strategy pages

Each strategy has a source file (`/strategies/<name>.md`) and an HTML page (`<name>.html`). The `.md` file is authoritative. When strategy facts change:

1. Update the `.md` file with the corrected information and note what changed and why
2. Update the corresponding `.html` file to match
3. Do not update the HTML without updating the `.md`

### Research Sources Convention

When a strategy page requires external research, the URLs used are stored inside the strategy's `.md` file in an HTML comment block. This block is never ported to HTML.

```markdown
<!-- RESEARCH SOURCES: internal reference only, do not port to HTML -->
- https://example.com/article (what this source contributed)
<!-- END RESEARCH SOURCES -->
```

Rules:
1. The block is placed at the top of the `.md` file, immediately after the frontmatter metadata fields
2. Each line is one URL with a parenthetical note on what the source contributed
3. When porting content from `.md` to `.html`, the `<!-- RESEARCH SOURCES -->` block and everything inside it is omitted entirely
4. Additional sources discovered later are added to the block in the `.md` file

### Writing Style

The following rules apply to all copy in HTML pages and documentation files. The `/strategies/*.md` source files should also follow these rules.

**Em dashes are prohibited.** Do not use the literal Unicode em dash character (U+2014, typed as —) or the HTML entity (`&mdash;`). Do not use double hyphens (`--`) as punctuation (CSS custom properties like `--color-accent` are valid CSS syntax and are not affected by this rule).

Use the following alternatives based on context:

| Situation | Replacement | Example |
|-----------|-------------|---------|
| Introducing a list, explanation, or elaboration after a complete clause | Colon | "The strategy uses three instruments: TQQQ, UVXY, and TLT." |
| Connecting two closely related independent clauses | Semicolon | "The plan targets 9% quarterly growth; actual returns vary significantly." |
| Parenthetical aside or supplementary information | Parentheses | "TQQQ (the ProShares UltraPro QQQ 3x ETF) resets its leverage daily." |
| Natural continuation where the sentence flows without emphasis | Comma | "The strategy enters bull mode, rotating fully into TQQQ." |
| When two thoughts are clearly separate sentences | Period | "The signal fires quarterly. The bond buffer absorbs the purchase." |

Both the literal character (—) and the HTML entity (`&mdash;`) must be searched independently when auditing copy, since a search for one will not find the other.

**Tone:** Direct, educational, attribution-first. No hype, no urgency, no calls to action. Present strategy mechanics neutrally. State risks clearly.

**Tense:** Past tense for historical events. Present tense for rules and mechanics. Avoid future tense for predictions.

**Attribution:** Credit original strategy authors by name and year. Credit source material (books, threads, papers) in the Resources section of each strategy page.

---

## 17. Press Release

**FOR IMMEDIATE RELEASE**

**Azqato Launches Leveraged Strategies: A Free, Hype-Free Reference for Six Major Leveraged ETF Strategy Frameworks**

*The new site documents the mechanics of TQQQ FTLT, HFEA, the 9 Sig plan, and three related strategies in one clean, consistent reference.*

**ONLINE, June 2026:** Azqato today launched Leveraged Strategies (https://azqato.github.io/leverage/), a free educational reference documenting six of the most widely discussed leveraged ETF strategy frameworks: the 3 Sig, 6 Sig, and 9 Sig quarterly value-averaging plans by Jason Kelly; TQQQ For The Long Term by u/derecknielsen; the Holy Grail variant; and Hedgefundie's Excellent Adventure (HFEA). The site provides mechanics-first documentation of each strategy, including allocation rules, decision trees, rebalancing cadences, historical backtest data, and risk factors, with no marketing language, no registration required, and no paid tier.

Information about leveraged ETF strategies is currently scattered across Reddit threads, paywalled newsletters, YouTube videos, and community backtesting tools with inconsistent methodology. Investors who want to understand how these strategies actually work must piece together information from many sources, many of which contain errors. Azqato Leveraged Strategies consolidates this information into a single, cleanly structured reference where each strategy is documented in the same five-section format: Overview, Rules and Logic, Performance Notes, Risks and Caveats, and Resources.

"I spent weeks trying to understand the actual rules of 9 Sig before I found Jason Kelly's original subscriber content," said a self-directed investor who reviewed the site before launch. "Having it documented clearly in one place, with the safeguards explained and the risks spelled out honestly, is exactly what I needed before putting money in."

The site is available now at https://azqato.github.io/leverage/. No account required.

**About Azqato**
Azqato builds free educational resources for self-directed investors. Properties include Leveraged Strategies (https://azqato.github.io/leverage/), Individual Stocks methodology documentation, and ComposerAtlas. All content is educational and does not constitute financial advice.

---

## 18. Frequently Asked Questions

### External FAQ (for site visitors)

**What is Leveraged Strategies?**
Leveraged Strategies is a free educational reference that documents six major leveraged ETF strategy frameworks: 3 Sig, 6 Sig, 9 Sig, TQQQ For The Long Term, Holy Grail, and HFEA. Each strategy has its own dedicated page documenting how it works, its historical performance characteristics, and its specific risks.

**Is this financial advice?**
No. This site is educational only. It documents how strategies work; it does not recommend that anyone follow any of them. All leveraged ETF strategies carry significant risk. Read the risk callout on every page before reading any strategy content.

**Are the strategies on this site the same as the original community versions?**
The site documents each strategy as close to its original specification as the primary sources allow. Where community backtesting has identified errors in common implementations (as documented in the BestFolio corrected backtest), those corrections are noted.

**Do I need to subscribe to anything to follow these strategies?**
The 3 Sig, 6 Sig, and 9 Sig plans are fully documented on this site. However, the official weekly signal values for these plans are published only in Jason Kelly's paid newsletter, The Kelly Letter. The TQQQ FTLT and Holy Grail strategies run on Composer.trade, which requires an account. HFEA can be implemented independently through any brokerage that offers UPRO and TMF.

**Why is there no live signal tracker or current allocation display?**
The site deliberately omits live data. Real-time signals go stale immediately and would require ongoing maintenance. The goal is documentation that remains accurate for years, not a dashboard that needs weekly updates.

**How often is the content updated?**
Content is updated when strategy rules change (rare) or when errors are identified and corrected. Historical backtest data is not updated to reflect new market conditions; figures reflect the backtest period cited.

**Are these strategies safe?**
No leveraged ETF strategy is safe in the conventional sense. TQQQ lost approximately 77% of its value in 2022. The HFEA portfolio lost approximately 65% in the same year. 9 Sig's closed-system simulation shows a median drawdown of approximately 98% in an extended bear scenario similar to the dot-com collapse. The strategies are documented here because they are well-known and interesting, not because they are recommended.

**What is the difference between the 3 Sig, 6 Sig, and 9 Sig strategies?**
All three use the same value-averaging signal mechanism created by Jason Kelly. The difference is the leverage tier: 3 Sig uses IJR/SPY (unleveraged), 6 Sig uses MVV (2x leveraged), and 9 Sig uses TQQQ (3x leveraged). The quarterly growth target scales accordingly: 3%, 6%, and 9%. Higher leverage produces higher potential returns and higher potential losses.

**What is TQQQ?**
TQQQ is the ProShares UltraPro QQQ ETF. It delivers approximately 3x the daily return of the Nasdaq-100 index. It uses daily rebalancing to achieve this, which means it is not suitable for passive buy-and-hold over long periods in sideways or volatile markets due to volatility decay.

**What is HFEA?**
HFEA stands for Hedgefundie's Excellent Adventure. It was proposed by a Bogleheads forum user in 2019. The strategy pairs UPRO (3x leveraged S&P 500) at 55% with TMF (3x leveraged long-duration Treasury bonds) at 45%, rebalanced quarterly. The thesis is that Treasuries historically uncorrelated with equities, meaning bond gains can offset equity losses in a crash. The 2022 bear market largely invalidated this correlation in practice.

**What is TQQQ FTLT?**
TQQQ For The Long Term is a daily rules-based algorithm created by Reddit user u/derecknielsen in October 2022. It uses SPY's 200-day simple moving average as a macro regime detector and 10-day RSI on multiple instruments for mean reversion signals. It rotates daily among six instruments: TQQQ, UVXY, TECL, UPRO, SQQQ, and TLT.

**What is the Holy Grail strategy?**
The Holy Grail is a variant of TQQQ FTLT that uses TQQQ's own 200-day SMA as the regime signal instead of SPY's, adds an SOXL mean reversion layer in bear mode, and uses BSV as the defensive instrument instead of TLT. It runs on Composer.trade.

**Can I implement these strategies in a regular brokerage account?**
The Kelly Signal plans (3 Sig, 6 Sig, 9 Sig) can be implemented in any brokerage that offers the relevant ETFs. TQQQ FTLT and Holy Grail require a platform that can execute algorithmic daily rules automatically; Composer.trade is the most commonly used platform. HFEA can be implemented manually through any brokerage.

**Does this site track me or collect my data?**
No. The site has no analytics, no tracking pixels, no cookies, no forms, and no user accounts. It is a static HTML site that loads no third-party scripts.

**Who built this site?**
Leveraged Strategies is built by Azqato. See also: Individual Stocks (https://azqato.github.io/stocks/) and ComposerAtlas (https://azqato.github.io/composer/).

**How do I report an error in the strategy documentation?**
Errors can be reported through the Support link in the navigation (https://azqato.github.io/support.html).

---

## 19. Version History

| Version | Date | Summary |
|---------|------|---------|
| Current | July 2026 | Full documentation audit; em dash cleanup; mobile CSS fix; semver patchnotes; this document |
| 1.4 | June 2026 | Marked M3 milestone complete; added live site URL; updated success criteria |
| 1.3 | June 2026 | Updated scope to six strategies and seven pages; marked M1/M2 complete |
| 1.2 | June 2026 | Added HFEA to pages table; documented Research Sources Convention |
| 1.1 | June 2026 | Added 3 Sig and 6 Sig pages; documented /strategies convention; Support link added |
| 1.0 | June 2026 | Initial PRD. Four-page scope, placeholder-first build, content philosophy and technical constraints defined |
