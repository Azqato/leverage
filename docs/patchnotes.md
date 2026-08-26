# PATCHNOTES.md: Leveraged Strategies Site

Format: reverse chronological order. Semver (MAJOR.MINOR.PATCH). Each entry has a date (YYYY-MM-DD) and changes grouped by Added, Changed, Fixed, Removed. Prior milestone-numbered versions (M1.x, M3.x) are preserved with semver equivalents noted.

---

## [v1.2.0] 2026-08-25: Documentation audit (second pass)

Comprehensive second documentation audit. Six new sections added to PRD.md. README rewritten for a general reader. DESIGN.md updated with new component and code block em dash fixes. No changes to HTML pages or CSS beyond what was already live.

### Added
- `docs/PRD.md §20`: Conventions: naming, formatting, organization, comment density, error handling, commit message style; all derived from codebase
- `docs/PRD.md §21`: Browser Testing: Microsoft Edge as the designated test browser; manual test checklist at five viewport sizes
- `docs/PRD.md §22`: Deprecation and Removal: public surface table, redirect policy (tombstone required for removed strategy pages), compatibility entry rules, retired items log
- `docs/PRD.md §23`: Documentation Versus Reality: discrepancy table comparing docs against code; 8 entries, 7 resolved, 1 open (reference/ folder)
- `docs/PRD.md §24`: Risks and Open Questions: fragile areas (nav duplication, strategies drift, single CSS file, no automated testing); 4 open questions; 2 answered questions preserved
- `docs/PRD.md §25`: Working Practice: read-before-editing table, non-negotiable rules, verification checklist, post-change update checklist
- `docs/DESIGN.md §7`: `.strategy-source-link` component documented (added in v1.1.1, was missing from design spec)

### Changed
- `README.md`: rewritten for a general reader; developer content (install steps, commands, env vars, build instructions) removed; all developer documentation lives in `docs/PRD.md §13`
- `docs/PRD.md §11`: session handoff note cleaned up; forward-looking items removed; completed work noted; pending decisions answered and filed in §24
- `docs/PRD.md §11`: roadmap table updated with v1.1.1 (Complete) and v1.2.0 (Complete) rows
- `docs/PRD.md §11`: current phase description updated to reflect v1.2.0
- `docs/PRD.md §14`: third-party integrations table updated with `composeratlas.com` row (added in v1.1.1, was missing)
- `docs/PRD.md §18`: TQQQ FTLT FAQ answer updated to mention the direct Composer link
- `docs/PRD.md §19`: version history table updated with v1.1.1 and v1.2.0 entries
- `docs/DESIGN.md §7`: strategy cards component spec: em dashes in pseudocode (`.card-title — 1.0625rem`) replaced with colons (`.card-title: 1.0625rem`)
- `docs/DESIGN.md §13`: CSS File Structure updated to include `.strategy-source-link` entry

---

## [v1.1.1] 2026-07-09: TQQQ FTLT Composer link

### Added
- `tqqq-ftlt.html`: link to original strategy on ComposerAtlas added near top of page, between hero and Overview section
- `css/style.css`: `.strategy-source-link` style added

---

## [v1.1.0] 2026-07-08: Documentation audit, em dash cleanup, mobile CSS fix

Full documentation overhaul. All four required documents rewritten to a comprehensive standard. Em dashes eliminated across all HTML pages and documentation files. Mobile table scrolling bug fixed for the 769px to 1023px viewport gap.

### Added
- `docs/PRD.md`: complete rewrite with all required sections: Problem Statement, Target Users, Goals, Non-Goals, User Stories, Feature List (MVP and Future), Constraints, Assumptions, Success Criteria, Tenets, Roadmap, Metrics, Runbook, Technical Requirements, Security, Press Release, FAQ, and Writing Style
- `docs/DESIGN.md`: complete rewrite with all required sections: Design Philosophy, Color Palette, Typography, Spacing System, Breakpoints, Component Patterns (full spec for every component), Accessibility Standards, Animation and Motion, and AI Context
- `docs/PATCHNOTES.md`: reformatted from milestone-numbered versioning to semver; all history preserved; this entry

### Changed
- `README.md`: complete rewrite: added Prerequisites, Installation, Environment Variables, Project Structure, Pages table, Adding a Strategy guide, Build and Deploy instructions, and Rollback instructions; removed marketing language; developer-focused throughout
- All 7 HTML pages: em dashes (Unicode U+2014) replaced with contextually appropriate punctuation per file (see em dash detail section below)

### Fixed
- `css/style.css`: `.table-wrap` had `overflow: hidden` in the base rule and `overflow-x: auto` only in the `max-width: 768px` block. At viewport widths 769px to 1023px, the layout is single-column (sidebar hidden) but tables could not scroll horizontally. Fixed by adding `overflow-x: auto; -webkit-overflow-scrolling: touch;` to the `max-width: 1024px` block.

### Em dash replacements by file
- `index.html`: lead paragraph, comma: `distinct approach, from quarterly`
- `3sig.html`: title colon; signal line comma; closed-system parentheses; 30 Down Rule semicolons; COVID crash comma; risk callout semicolons; BestFolio h3 colon; resource list colons throughout
- `6sig.html`: title colon; mechanics parentheses; MVV appositive comma; BestFolio h3 colon; bond buffer comma; resource list colons
- `9sig.html`: title colon; safeguards colon+comma; TQQQ appositive parentheses; core mechanics parentheses; ratio drift colon; 30 Down Rule semicolon; BestFolio h3 colon; internal quote colon; risk callout semicolons; resource list colons
- `tqqq-ftlt.html`: title colon; meta description comma; SMA sentence parentheses; October 2022 comma; Step 1 period; academic h3 colon; risk callout semicolon; backtest window comma; Great Depression comma; resource list colons
- `hfea.html`: title colon; regime-adaptive h3 colon; TMV appositive comma; bond decline semicolon
- `holy-grail.html`: title colon; meta description comma; event-driven colon+comma; primary regime comma; bull regime semicolon; Step 1 period; SOXL colon; academic h3 colon; resource list colons

---

## [v1.0.4] 2026-07-08: Repository rename (formerly M3.4)

### Changed
- `README.md`: live site URL and repository URL updated from `leveraged-strategies` to `leverage`
- `docs/patchnotes.md`: URLs updated
- `docs/prd.md`: live site URLs updated
- Git remote `origin` updated to `https://github.com/Azqato/leverage`

---

## [v1.0.3] 2026-06-15: Cross-site nav links (formerly M3.3)

### Changed
- All 7 HTML pages: two nav items added above Support in both sidebar and top-bar nav: "Individual Stocks" linking to `https://azqato.github.io/stocks/` and "ComposerAtlas" linking to `https://azqato.github.io/composer/`

---

## [v1.0.2] 2026-06-10: Site rename to Leveraged Strategies (formerly M3.2)

### Changed
- All 7 HTML pages: `<title>` and `.site-label` span updated from "TQQQ Strategies" to "Leveraged Strategies"
- `index.html`: `<h1>` heading updated
- `README.md`: top-level heading updated
- `docs/DESIGN.md`, `docs/PRD.md`, `docs/PATCHNOTES.md`: document titles updated

---

## [v1.0.1] 2026-06-10: Docs sync and GitHub Pages launch (formerly M3.1)

### Changed
- `README.md`: status updated to Live; live site URL and repository URL added
- `docs/PRD.md`: M3 milestone marked Complete; success criteria updated with live URL

---

## [v1.0.0] 2026-06-10: Full content port, major release (formerly M3.0)

All seven HTML pages rewritten with full strategy content. Every placeholder replaced. Four hero badge and lead paragraph corrections applied.

### Added
- `index.html`: all six strategy cards rewritten with accurate summaries, tickers, and rebalancing cadences
- `3sig.html`: full five-section content port: allocation table (80/20 IJR/SPY), signal line formula, quarterly buy/sell table, 30 Down Rule (4 ignores, no reset), BestFolio backtest (CAGR 9.0%, max DD −52.3%, Sharpe 0.31)
- `6sig.html`: full five-section content port: allocation table (60/40 MVV/bonds), 6% quarterly signal, 30 Down Rule (2 ignores, resets to 60/40), BestFolio backtest (CAGR 11.7%, max DD −78.3%, Sharpe 0.23), plan family comparison table
- `9sig.html`: full five-section content port: allocation (60/40 TQQQ/bonds), both safeguards (90% throttle and Spike Reset), 30 Down Rule (2 ignores, resets to 60/40), Kelly Letter portfolio tracking ($733k Jan 2018 to $5.9m Dec 2024), BestFolio backtest (CAGR 39.4%, max DD −72.1%, Sharpe 0.82), dot-com simulation, closed-system bootstrap
- `tqqq-ftlt.html`: full five-section content port: instruments table, signal inputs table, full bull/bear decision trees, 10-year backtest (TQQQ FTLT +298% vs. TQQQ buy-and-hold +35%), Gayed and Bilello LRS academic table (87-year backtest)
- `hfea.html`: full five-section content port: both allocations (40/60 and 55/45), cost-of-leverage table, community variants table, HFEA The Resurrection regime-adaptive variant (four regimes driven by SPY 200D SMA and TLT 400D SMA), live tracking table (May 2019 to April 2025)
- `holy-grail.html`: full five-section content port: instruments table, full bull (80%) and bear decision trees with SOXL oversold layer, comparison table vs. TQQQ FTLT

### Fixed
- `3sig.html` and `6sig.html` hero badges: "Monthly Rebalancing" changed to "Quarterly Rebalancing"
- `tqqq-ftlt.html` hero badge: "Buy and Hold" changed to "Daily Algorithm"; lead paragraph corrected
- `holy-grail.html` hero badge: "Rules-Based Allocation" changed to "Event-Driven Algorithm"; lead paragraph corrected; TMF removed (not used in this strategy)
- All 7 pages: all placeholder blocks removed

---

## [v0.1.8] 2026-06-10: HFEA rename and Composer variant (formerly M1.8)

### Added
- `strategies/hfea.md`: "Regime-adaptive variant" subsection: HFEA The Resurrection by u/derecknielsen, four-regime table driven by SPY 200D SMA and TLT 400D SMA

### Changed
- `strategies/hefa.md` renamed to `strategies/hfea.md`; `hefa.html` renamed to `hfea.html`
- All 7 pages, `css/style.css`, `README.md`, `docs/PRD.md`, `docs/DESIGN.md`: hefa references updated to hfea

---

## [v0.1.7] 2026-06-10: Documentation sync (formerly M1.7)

### Changed
- `README.md`: pages table expanded to 7 pages; TQQQ FTLT description corrected; status updated
- `docs/PRD.md`: goals, functional requirements, and milestones updated to reflect six strategies and seven pages
- `docs/DESIGN.md`: HFEA orange tint token added; version history updated

---

## [v0.1.6] 2026-06-10: Holy Grail full content (formerly M1.6)

### Added
- `strategies/holy-grail.md`: full five-section content written. Instruments: TQQQ, UVXY, TECL, SOXL, SQQQ, BSV. Full decision tree from Composer JSON. Metadata corrections for HTML port documented.

---

## [v0.1.5] 2026-06-10: TQQQ FTLT full content (formerly M1.5)

### Added
- `strategies/tqqq-ftlt.md`: full five-section content written. Strategy is daily algorithmic (corrected from buy-and-hold placeholder). Full decision tree from Composer JSON and original Reddit post.

---

## [v0.1.4] 2026-06-10: 3 Sig, 6 Sig, 9 Sig full content (formerly M1.4)

### Added
- `strategies/3sig.md`: full content: 80/20 IJR/SPY, 3% quarterly signal, 30 Down Rule (4 ignores, no reset), BestFolio backtest, 17 research sources
- `strategies/6sig.md`: full content: 60/40 MVV/bonds, 6% quarterly signal, 30 Down Rule (2 ignores, resets to 60/40), BestFolio backtest
- `strategies/9sig.md`: full content: 60/40 TQQQ/bonds, 9% signal, 90% throttle, Spike Reset, BestFolio backtest, dot-com simulation, closed-system bootstrap

---

## [v0.1.3] 2026-06-10: HFEA content and research sources convention (formerly M1.3)

### Added
- `strategies/hefa.md`: full five-section content. Risk parity basis. Both allocations (40/60 and 55/45). BestFolio backtest (23.75% CAGR). Lost-decade validation. Cost-of-leverage table. Live tracking table.
- `docs/PRD.md`: Research Sources Convention section: URLs stored in `<!-- RESEARCH SOURCES -->` comment blocks in .md files, never ported to HTML

---

## [v0.1.2] 2026-06-10: HFEA page (formerly M1.2)

### Added
- `hefa.html`: HFEA strategy page (placeholder sections, orange `#f0883e`, Quarterly Rebalancing badge, UPRO/TMF tickers)
- `strategies/hefa.md`: content source skeleton
- `css/style.css`: `--color-strat-hefa` token and `.strat-hefa::before` rule

### Changed
- All 6 existing pages: HFEA nav link added before Support

---

## [v0.1.1] 2026-06-10: 3 Sig, 6 Sig, nav convention, footer and support link (formerly M1.1)

### Added
- `3sig.html`: placeholder page, light blue `#79c0ff`
- `6sig.html`: placeholder page, amber `#e3b341`
- `strategies/3sig.md`, `strategies/6sig.md`: content source skeletons
- Support link (`https://azqato.github.io/support.html`) added as permanent last nav item

### Changed
- `index.html`: 3 Sig and 6 Sig cards added; nav updated
- `9sig.html`, `tqqq-ftlt.html`, `holy-grail.html`: nav updated with 3 Sig and 6 Sig links
- All pages: footer updated to "Built by Azqato." pattern
- `css/style.css`: `--color-strat-3sig` and `--color-strat-6sig` tokens added
- `docs/DESIGN.md`, `docs/PRD.md`: tint table, footer, and nav convention documented

---

## [v0.1.0] 2026-06-10: Initial skeleton build (formerly M1.0)

### Added
- `index.html`: home page with three strategy cards (9 Sig, TQQQ FTLT, Holy Grail) and leveraged ETF risk callout
- `9sig.html`, `tqqq-ftlt.html`, `holy-grail.html`: strategy pages with placeholder sections and mandatory risk callout
- `css/style.css`: full shared stylesheet: design tokens, reset, layout grid, sidebar, top-bar nav, typography, hero, strategy cards, placeholder blocks, tables, callout boxes, badges, ticker tags, footer, responsive breakpoints, reduced-motion
- `js/main.js`: IntersectionObserver anchor highlighting; mobile nav toggle
- `strategies/9sig.md`, `strategies/tqqq-ftlt.md`, `strategies/holy-grail.md`: content source skeletons
