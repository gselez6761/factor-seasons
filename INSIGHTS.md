# Factor Seasons · Four Findings

**Page:** `insights.html`
**Companion to:** `index.html` (the full scrollytelling version)
**CMSC 471 · Spring 2026 · Team 10**

---

## What this page is

`insights.html` is a tightened, editorially-driven companion to the main `index.html` page.
The full version contains a 14-step scrollytelling tour, a recession scorecard, regime
bar charts, an annual heatmap, and a 25-portfolio explorer - useful breadth, but enough
surface area that a first-time reader can lose the thread.

This page strips that down to **four findings**, each accompanied by exactly one chart,
each chosen because it says something a person who has never opened a brokerage account
would not have guessed. The visual language is modeled on a Wall Street Journal interactive
feature: cream background, Playfair Display serif headlines, IBM Plex Sans for data labels,
muted editorial factor palette (navy, burnt orange, forest green, brick red, slate purple,
wine), thin double-rule section breaks, and a WSJ-red accent.

---

## The four findings

### Finding 01 - The Sixty-Year Race
A log-scale cumulative growth chart. Six factors, sixty-two years, **$1 starting capital**.
The end values: Momentum $44.47, Market $40.15, Value $6.55, Profitability $6.14,
Investment $5.55, **Size $2.83**. The momentum cliff in 2009 is visible as a vertical drop.
The Size factor's flatlining is visible as the bottom line.

> **Caveat printed on the page:** these are *academic long-short factor returns* - frictionless,
> costless, and not directly investable. Real-world factor ETFs underperform academic returns
> by roughly 0.5–2% per year due to financing, transaction costs, and short-borrow fees.

### Finding 02 - The Disagreement
An annual heatmap (62 years × 6 factors) with a "Year's leader" colored strip beneath it
and four key-year annotations (1980 Volcker, 1999 Dot-com peak, 2008 Financial Crisis, 2020
COVID). Headline stat in the deck:

> **In only 13 of 752 months did all six factors move the same direction** (12 positive, 1 negative).

Independent random chance would predict 3.7% all-aligned with these per-factor hit rates.
Observed is 1.7%. So factors are *more* divergent than independence would predict.

### Finding 03 - The Rotation
A decade-by-decade horizontal bar chart, 7 decades × 6 factors, using **compound** returns
(not summed). The 2000s row is highlighted because it is the only decade in which the
Market itself was the losing factor:

> **Market lost 27%. Profitability gained 108%. A 135-percentage-point gap, for an entire decade.**

Hover any factor in any decade for the historical context - real macroeconomic events
(oil shocks, Volcker, Reagan-era LBOs, dot-com, GFC, ZIRP, COVID, AI boom) are tied to the
factor performance directly.

The chart also reveals that **Momentum lost money in the 2000s in compound terms** (−19%)
because April 2009's −34% crash erased years of small monthly gains - a fact obscured if
you sum monthly returns instead of compounding them.

### Finding 04 - Market vs. Quality
Two side-by-side bar charts - calm markets (VIX below sample median 17.5) on the left,
fearful markets (VIX above) on the right, both sorted within-panel. Covers **1990–2025**
(the VIX-publication era). The story is narrower than "everything flips":

> **Only Market and Profitability swap places.** Market goes from best (+1.70%/mo) in calm
> to worst (−0.23%/mo) in fearful. Profitability goes from middle to top. The other four
> factors barely move.

Hover any factor for the mechanism - flight-to-quality for RMW, cyclical-stress story for
Value, aggressive-firm-repricing for CMA, etc.

---

## Closing thought

The page ends with a single editorial paragraph: *no factor wins every season, the factors
are imperfectly correlated, owning more than one is the whole point.* This is empirical, not
financial advice - the data show that factor diversification reduces concentration risk
across most decades, with notable failures (e.g., 2008–09 when correlations spiked).

---

## Files used

```
insights.html              ← this page (single self-contained HTML+CSS+JS file)
data/cumulative_6f.json    ← Finding 1: compounded factor returns since July 1963
data/annual_6f.json        ← Finding 2: annual returns by factor and year
data/monthly_6f_regimes.json ← Findings 3 and 4: monthly returns + regime labels
```

The four charts are independently rendered by four functions: `renderCumulative()`,
`renderHeatmap()`, `renderDecades()`, `renderVixFlip()`. All rendering is done with D3 v7.
No build step.

---

## Running

```bash
cd factorseasons
python3 -m http.server 8080
# then open http://localhost:8080/insights.html
```

The data is served as static JSON via the same web server. Opening directly via `file://`
will not work because of `d3.json()` fetch requirements.

---

## How this page differs from `index.html`

|  | `index.html` | `insights.html` |
|---|---|---|
| **Format** | 14-step scrollytelling | 4 standalone findings |
| **Charts** | 8+ chart types | 4 chart types |
| **Theme** | Dark (early version) → WSJ editorial (current) | WSJ editorial only |
| **Audience focus** | Anyone, deep dive | Newcomer, single-pass |
| **Reading time** | 12–15 min | 8 min |
| **Insights** | Many, broad | 4, sharp |

`index.html` is preserved unchanged as the broader exploration. `insights.html` is the
"what would a journalist write?" cut.

---

## Validation

Every quantitative claim on this page has been verified against the source data via Python.
A CFA-style audit was performed before publication (see `AI_USAGE.md` for details). The most
important correction made during that audit was switching Finding 3 from arithmetic-summed
returns to compounded returns - which materially changed several numbers (most dramatically,
Momentum's 2000s went from a small *positive* in summed terms to a clear *loss* in compound
terms).
