# Leveraged Strategies

A static, multi-page educational reference site covering six leveraged ETF strategies. Built with vanilla HTML, CSS, and JavaScript. No frameworks, no build tools, no dependencies.

**Live site:** https://azqato.github.io/leverage/
**Repository:** https://github.com/Azqato/leverage
**Full documentation:** [/docs](docs/)

---

## What this site is

A methodology library for six distinct leveraged ETF strategies. Each strategy has its own dedicated page with a consistent five-section structure: overview, rules and logic, performance notes, risks and caveats, and resources. The site is educational. It documents strategy frameworks, not live positions or recommendations.

---

## Tech stack

| Layer | Technology | Version |
|-------|-----------|---------|
| Markup | HTML5 | — |
| Styles | CSS3 (custom properties, grid, flexbox) | — |
| Scripts | Vanilla JavaScript (ES5-compatible) | — |
| Hosting | GitHub Pages | — |
| Build | None | — |
| Package manager | None | — |
| Dependencies | None | — |

No Node, no npm, no bundler. The repo is the deployable artifact.

---

## Prerequisites

- A modern browser (for local development)
- Python 3 (optional, for a local dev server with correct MIME types)
- Git (to clone and push)

No runtime, no environment variables, no API keys.

---

## Installation

```bash
git clone https://github.com/Azqato/leverage.git
cd leverage
```

That is the complete installation. There is nothing to install.

---

## Running locally

Option A: open `index.html` directly in a browser. This works for browsing but may produce MIME-type warnings in some browsers for the CSS/JS files.

Option B (recommended): serve via Python's built-in HTTP server.

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000` in a browser.

No hot reload, no dev server configuration, no environment setup required.

---

## Environment variables

None. This project has no server-side code, no API keys, no secrets, and no environment-specific configuration. Do not create a `.env` file; there is nothing to put in it.

---

## Project structure

```
/
├── index.html              Home page
├── 3sig.html               3 Sig strategy page
├── 6sig.html               6 Sig strategy page
├── 9sig.html               9 Sig strategy page
├── tqqq-ftlt.html          TQQQ FTLT strategy page
├── holy-grail.html         Holy Grail strategy page
├── hfea.html               HFEA strategy page
├── css/
│   └── style.css           Single shared stylesheet (all design tokens + components)
├── js/
│   └── main.js             Single shared script (scroll highlighting, mobile nav)
├── strategies/
│   ├── 3sig.md             Content source for 3sig.html
│   ├── 6sig.md             Content source for 6sig.html
│   ├── 9sig.md             Content source for 9sig.html
│   ├── tqqq-ftlt.md        Content source for tqqq-ftlt.html
│   ├── holy-grail.md       Content source for holy-grail.html
│   └── hfea.md             Content source for hfea.html
├── docs/
│   ├── PRD.md              Product requirements and full project documentation
│   ├── DESIGN.md           Design system, tokens, and component specifications
│   └── PATCHNOTES.md       Changelog
└── README.md               This file
```

The `/strategies` directory holds source-of-truth markdown for each strategy. These are reference documents used when authoring or updating HTML content, not live-rendered files. Each includes a `<!-- RESEARCH SOURCES -->` comment block with research URLs that must never be ported to HTML.

---

## Pages

| Page | File | Description |
|------|------|-------------|
| Home | `index.html` | Landing hub with strategy cards and leveraged ETF risk callout |
| 3 Sig | `3sig.html` | Quarterly value-averaging signal plan (unleveraged, IJR/SPY) |
| 6 Sig | `6sig.html` | Quarterly value-averaging signal plan (2x leveraged, MVV) |
| 9 Sig | `9sig.html` | Quarterly value-averaging signal plan (3x leveraged, TQQQ) |
| TQQQ For The Long Term | `tqqq-ftlt.html` | Daily rules-based algorithm using SMA regime switching and RSI mean reversion |
| Holy Grail | `holy-grail.html` | TQQQ FTLT variant using TQQQ's own 200D SMA, SOXL mean reversion, and 20% cash buffer |
| HFEA | `hfea.html` | 55% UPRO / 45% TMF quarterly-rebalanced leveraged risk parity portfolio |

---

## Adding a new strategy

1. Create `/strategies/<name>.md` as the content source, following the existing file structure
2. Create `<name>.html` at the repo root using an existing strategy page as the template
3. Add a nav `<li>` to every existing page (sidebar and top-bar nav), before the Individual Stocks link
4. Add a strategy card to `index.html`
5. Add a CSS token `--color-strat-<name>` and corresponding `::before` rule in `style.css`

The Support link is always the last nav item.

---

## Build and deploy

There is no build step.

To deploy: push to the `main` branch. GitHub Pages is configured to serve from the repo root. Changes go live within a few minutes of the push completing.

```bash
git add .
git commit -m "describe what changed"
git push origin main
```

The live site URL is: https://azqato.github.io/leverage/

---

## Rollback

To revert to a previous version, reset to the target commit and force-push (confirm with the team before doing this):

```bash
git log --oneline          # find the target commit hash
git reset --hard <hash>
git push --force origin main
```

Alternatively, revert a specific commit without rewriting history:

```bash
git revert <hash>
git push origin main
```

---

## Disclaimer

Educational use only. Nothing on this site is financial advice. Leveraged ETFs carry significant risk including volatility decay and amplified drawdowns. See the risk callout on every page.
