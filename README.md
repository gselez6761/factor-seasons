# Factor Seasons

**Visualizing When Risk Premiums Appear and Disappear**

CMSC 471 - Introduction to Information Visualization · University of Maryland · Spring 2026 · Team 10

---

Factor Seasons is an interactive data visualization exploring 62 years of equity factor returns. The page presents four findings drawn from monthly Fama-French factor data (July 1963 - December 2025), showing how factor performance shifts across economic regimes - recessions, rate cycles, and volatility spikes.

The six factors covered: Market (Mkt-RF), Size (SMB), Value (HML), Profitability (RMW), Investment (CMA), and Momentum.

---

## Team

Gregory Seleznev, Martin Ye, Alex Dong

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

- **Ken French Data Library** - monthly factor returns (Mkt-RF, SMB, HML, RMW, CMA, Mom)
- **FRED / NBER** - recession indicator (USREC)
- **CBOE** - VIX monthly volatility index (from 1990)
