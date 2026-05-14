# Factor Seasons

**Visualizing When Risk Premiums Appear and Disappear**

CMSC 471 - Introduction to Information Visualization · University of Maryland · Spring 2026 · Team 10

---

Factor Seasons is an interactive data visualization exploring 62 years of equity factor returns. The page presents four findings drawn from monthly Fama-French factor data (July 1963 - December 2025), showing how factor performance shifts across economic regimes - recessions, rate cycles, and volatility spikes.

The six factors covered: Market (Mkt-RF), Size (SMB), Value (HML), Profitability (RMW), Investment (CMA), and Momentum.

---

## Team

| Name | Contribution |
|---|---|
| Gregory Seleznev | Data pipeline (Python) - downloading, cleaning, and merging all datasets; page architecture and layout; all four D3 visualizations; narrative text; visual design and CSS |
| Martin Ye | Legend on the cumulative returns chart; timeframe selector (slider) on the cumulative returns chart; highlight effect toggle button on the cumulative returns chart |
| Alex Dong | Iterative design feedback and review across all visualizations |
---

## Running

Static site - no build step needed.

```bash
python3 -m http.server 8080
# Open http://localhost:8080
```

Must be served over HTTP (not `file://`) because the app loads JSON data with `d3.json()`.

---

## Data Sources

- **[Ken French Data Library](https://mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html)** - monthly factor returns (Mkt-RF, SMB, HML, RMW, CMA, Mom)
- **[FRED / NBER](https://fred.stlouisfed.org/series/USREC)** - recession indicator (USREC)
- **[CBOE VIX](https://www.cboe.com/tradable_products/vix/)** - monthly volatility index (from 1990)
