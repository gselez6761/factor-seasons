# Factor Seasons

**Visualizing When Risk Premiums Appear and Disappear**

CMSC 471 - Introduction to Information Visualization · University of Maryland · Spring 2026 · Team 10

---

## Description

Factor Seasons is a scrollytelling, interactive visualization that makes the time-varying, regime-dependent nature of equity factor returns legible to someone who has never taken a finance class. Users scroll through a guided narrative covering 60+ years of factor performance data, discovering how the six Fama-French factors behave across economic regimes - recessions, rate cycles, and volatility spikes.

### Key questions explored:
- Why did Value stocks lose money for 7 straight years (2013–2020) before staging a massive recovery?
- Why did Momentum - the highest-performing factor for 40 years - crash 83% in just 6 months in 2009?
- How do factor returns systematically differ across recession/expansion, rising/falling rates, and high/low volatility?

---

## Team Members

| Name | GitHub |
|---|---|
| Gregory Seleznev | - |
| Martin Ye | - |
| Alex Dong | - |

---

## Running Instructions

This is a static web application - no build step, no server required.

**Option 1 - Python local server (recommended):**
```bash
cd factorseasons
python3 -m http.server 8080
# Open http://localhost:8080
```

**Option 2 - VS Code Live Server:** Open `index.html` with Live Server extension.

**Option 3 - GitHub Pages:** Push to a GitHub repo and enable Pages from the repo settings. The `index.html` and `data/` directory are all that's needed.

> Note: Opening `index.html` directly via `file://` will not work because the app fetches JSON data files with `d3.json()`, which requires an HTTP server.

---

## Project Structure

```
factorseasons/
├── index.html          # All visualization code (HTML + CSS + JS, single file)
└── data/
    ├── cumulative_6f.json          # Cumulative factor returns since 1963
    ├── monthly_6f.json             # Monthly factor returns
    ├── monthly_6f_regimes.json     # Monthly returns with regime labels (USREC, rate, VIX)
    ├── annual_6f.json              # Annual factor returns (heatmap source)
    ├── rolling_5yr_6f.json         # 5-year rolling annualized returns
    ├── recession_bands.json        # NBER recession start/end dates
    ├── portfolios_25.json          # 25 Size × Book-to-Market portfolios monthly returns
    ├── fedfunds.json               # Federal Funds Rate monthly
    ├── usrec.json                  # NBER recession indicator
    ├── vix.json                    # CBOE VIX monthly
    └── meta.json                   # Factor metadata
```

---

## Work Breakdown

| Component | Owner(s) | Notes |
|---|---|---|
| Data pipeline (Python) - downloading, cleaning, merging all datasets | Gregory | Fama-French, FRED, VIX, regime classification |
| Scrollytelling layout & IntersectionObserver | Gregory | Sticky chart + narrative steps |
| Animated cumulative returns chart | Gregory | D3 clipPath animation, annotation overlays |
| Legend and timeframe selector (context brush) on cumulative returns chart | Martin | |
| Iterative design and feedback on visualizations | Alex | |
| Narrative text & factor explanations | All | Plain-language accessible to non-finance audiences |
| Visual design & CSS | Gregory | Dark theme, responsive layout |

---

## Data Sources

- **Ken French Data Library** - Fama/French 5 Factors (2×3) Monthly, Momentum Factor Monthly, 25 Portfolios on Size and Book-to-Market
- **FRED (Federal Reserve Economic Data)** - NBER Recession Indicator (USREC), Federal Funds Rate (FEDFUNDS)
- **CBOE / Yahoo Finance** - VIX Index monthly

---

## Acknowledgements

- Eugene Fama & Kenneth French - foundational factor research (1992, 1993, 2015)
- Narasimhan Jegadeesh & Sheridan Titman - momentum factor (1993)
- D3.js by Mike Bostock
- Inspired by AQR Capital Management's factor research publications and The Idea Farm newsletter
- Built with assistance from Claude Code (Anthropic)

---

## AI Usage

Claude Code (Anthropic) was used to assist with:
- Scrollytelling architecture planning and D3.js implementation
- Regime annotation overlay design
- Compliance review against CMSC 471 project requirements

All data pipeline code, visual design decisions, and narrative content were produced by the team.
