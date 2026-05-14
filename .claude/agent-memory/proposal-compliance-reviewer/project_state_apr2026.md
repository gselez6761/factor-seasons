---
name: Project State April 2026
description: What is and isn't built in the Factor Seasons project as of the WSJ redesign review on 2026-04-30
type: project
---

Single-file build: index.html (WSJ editorial aesthetic, ~1,770 lines) + data/ JSON files. No external scrollytelling library — uses native IntersectionObserver.

**Data files present and loaded**: rolling_5yr_6f.json, annual_6f.json, monthly_6f_regimes.json, recession_bands.json, portfolios_25.json — all fetched in Promise.all. Also present but not directly fetched in JS (regime labels baked into monthly_6f_regimes): fedfunds.json, usrec.json, vix.json, cumulative_6f.json, meta.json.

**What IS built (as of 2026-04-30 WSJ redesign)**:
- Scrollytelling format: IntersectionObserver-driven 14-step narrative (steps 0–13), sticky chart pane, step cards that activate scenes. Proposal format requirement now met.
- Factor Introduction: Hero, lede, explainer box, 6 factor cards with 2x3 grid (scene-intro). Accessible language.
- Narrative callouts: All three required by proposal are present as dedicated scroll steps:
  - Step 9: Value drought 2013–2021 (value-drought mode, HML focused with shade band)
  - Step 10: Momentum crash 2009 -83% (momentum-crash mode, Mom focused with shade band)
  - Step 7: Value leads recession recovery (callout text in step 7 card)
- Rolling 5yr chart: Single-factor focus per factor step (1–6), multi-factor overlay steps (7, 9, 10), recession bands, per-factor annotations and stat boxes, crosshair tooltip.
- Recession scorecard heatmap: 8 recessions x 6 factors, total return per recession, GFC highlighted, tooltips.
- Regime bar charts: Business Cycle (USREC), Rate Environment (FEDFUNDS trend), VIX regime — steps 11–13.
- Annual heatmap: 62 years x 6 factors, RdYlGn diverging color scale, tooltips, labels every 5yr.
- 25 Portfolio Explorer: portfolios_25.json loaded and rendered, regime filter dropdown (7 options: all/expansion/recession/rates-rising/rates-falling/vix-low/vix-high), 5x5 heatmap with size/BM axis labels.
- All 6 factor series: Mkt-RF, SMB, HML, RMW, CMA, Mom — all rendered everywhere.
- All required datasets: Fama-French 5F+Mom, FRED USREC/FEDFUNDS, VIX — all present.
- Dynamic tooltips with exact values throughout.
- Responsive: mobile layout with sticky chart on top.

**What is still MISSING vs. proposal**:
1. Animated horse race — no play/pause cumulative animation. cumulative_6f.json exists but is never fetched or rendered. The rolling chart is present but not animated. Proposal asks for an "animated" cumulative performance comparison.
2. Interactive Factor Lab (optional/"may include") — not implemented. Users cannot weight factors and see backtested results.
3. Rolling correlations / user-adjustable time windows for statistics — not present. Proposal mentions "factor correlations across user-adjustable time windows, recalculated per economic environment."
4. VIX median hardcoded as 17.49 — acceptable simplification but worth noting.

**Why:** Items 2–3 are either optional or lower-priority. Item 1 (animated horse race) is described as required in the proposal but the current rolling chart partially serves this function narratively.

**How to apply:** Items 2–3 are bonus. Item 1 (animated cumulative chart) is the primary remaining gap from required features. Overall compliance is High given the scrollytelling, all datasets, all 6 factors, all narrative callouts, and the 25-portfolio explorer are now fully implemented.
