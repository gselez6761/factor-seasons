# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the project

This is a static web app — no build step, no package manager.

```bash
python3 -m http.server 8080
# Open http://localhost:8080
```

The app uses `d3.json()` to load data files, so it must be served over HTTP, not opened directly via `file://`.

## Architecture

Everything lives in `index.html` — HTML, CSS, and JavaScript are all in one file (~1650 lines). There is no bundler, framework, or transpilation.

**JavaScript structure** (bottom of `index.html`, inside `<script>`):

- `FACTORS` / `FM` — factor metadata (keys, labels, colors, descriptions)
- `C` — color palette constants mirrored from CSS custom properties
- `DB` — global data store; populated from `Promise.all([d3.json(...)])` at startup
- `buildFactorCards()` — renders the primer factor card grid
- `renderCumulative()` — Chart 1: log-scale cumulative return line chart with crosshair hover
- `renderVixFlip()` — Chart 2: side-by-side bar chart (calm vs. fearful VIX regimes)
- `renderHeatmap()` — Chart 3: annual returns color heatmap (RdYlGn, winner/loser toggle)
- `renderDecades()` — Chart 4: decade-by-decade compounded returns bar chart
- All four render functions are also wired to a debounced `window.resize` handler

Each chart function is self-contained: it queries its container `div` by ID, measures its width, builds a D3 SVG, and attaches mouse event listeners directly.

**Data files** (`data/` directory):

| File | Contents |
|---|---|
| `cumulative_6f.json` | Cumulative factor returns since 1963 (date + 6 factor columns) |
| `annual_6f.json` | Annual returns per factor (heatmap source) |
| `monthly_6f_regimes.json` | Monthly returns with `vix_regime`, `rec_regime`, `rate_regime` labels |
| `recession_bands.json` | NBER recession start/end date pairs |
| `fedfunds.json` | Federal Funds Rate monthly |
| `usrec.json` | NBER binary recession indicator |
| `vix.json` | CBOE VIX monthly |
| `portfolios_25.json` | 25 Size × Book-to-Market portfolio monthly returns |
| `meta.json` | Factor metadata |
| `rolling_5yr_6f.json` | 5-year rolling annualized returns |

Dates in JSON are `'YYYY-MM-DD'` strings; `pd = d3.timeParse('%Y-%m-%d')` converts them to JS Date objects at load time. Exception: `annual_6f.json` stores year as a Unix timestamp integer.

## Design system

CSS custom properties are defined on `:root` and mirrored as JS constants in `C`. Key tokens:

- `--bg` `#FAF9F7` / `--paper` `#FFFFFF` — page and card backgrounds
- `--accent` `#C8232C` — red accent (kickers, active states)
- `--pos` `#1A6B3C` / `--neg` `#A52313` — green/red for positive/negative values
- Fonts: `Playfair Display` (display headlines), `Source Serif 4` (body), `IBM Plex Sans` (labels/UI)

Factor colors are defined in `FM` (not in CSS) and must stay consistent across all four charts.

## Content structure

Four "insight" sections, each with a fixed narrative structure:
1. `insight-num` badge → `sec-label` kicker → `sec-headline` → `sec-deck` body text
2. Chart container div (populated by D3)
3. `figure-caption` with methodology notes and source attribution

The page is article-style (not scrollytelling with sticky panels) — all four charts are rendered immediately on load and remain in the DOM.

## Project context

CMSC 471 (Information Visualization) final project at University of Maryland, Spring 2026. The grading criteria and proposal are tracked by the `fp-compliance-checker` and `proposal-compliance-reviewer` agents in `.claude/agents/`.
