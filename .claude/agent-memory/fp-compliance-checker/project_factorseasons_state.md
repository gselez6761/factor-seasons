---
name: Factor Seasons project state as of 2026-05-13
description: CMSC471 Final Project current implementation status, compliance gaps, and rubric assessment one day before Demo Day (2026-05-14)
type: project
---

Team 10 (Gregory Seleznev, Martin Ye, Alex Dong). Canvas Group 10. "Team 10" visible in footer and README.

**Current state of index.html (single-file, 1656 lines):**
- WSJ editorial aesthetic: cream bg (#FAF9F7), Playfair Display + Source Serif 4 + IBM Plex Sans, drop cap lede, byline bar, sticky top bar (top bar HTML comment present but top-bar div is empty/commented out in HTML).
- Four-finding format (NOT scrollytelling anymore): Finding 01 cumulative race, Finding 02 Market vs. Quality (VIX flip), Finding 03 Disagreement heatmap, Finding 04 Decade Rotation.
- Four D3 charts: renderCumulative(), renderVixFlip(), renderHeatmap(), renderDecades().
- Interactions: hover tooltips on all charts, clickable legend on cumulative, All/Winners/Losers toggle on heatmap, animated bar entry transitions.
- Footer: team names, CMSC 471 course info, Team 10, data sources, acknowledgements (Fama/French, Daniel & Moskowitz, Asness et al., D3.js). Does NOT mention AQR/Idea Farm anymore.
- Byline in hero: all 3 author names.
- insights.html was DELETED (consolidated into index.html). INSIGHTS.md still exists as doc only.
- old_version.html exists in repo (the original dark-theme scrollytelling version).

**README.md:** Complete — title, description, team members (GitHub handles still dashes), running instructions, project structure, work breakdown table (per-member attribution), data sources, acknowledgements, AI usage section.

**AI_USAGE.md:** Excellent — 2 sessions documented, 9 specific corrections listed, tooling table, honest assessment section.

**Remaining gaps (day before Demo Day):**
1. GitHub Pages URL not confirmed deployed — README says Option 3 is GitHub Pages but no live URL is present anywhere.
2. Canvas submission: live demo URL + code repo URL must be submitted to Canvas-ELMS before demo session.
3. GitHub handles still dashes in README team table.
4. The `top-bar` HTML element exists in CSS but the HTML comment `<!-- TOP BAR -->` is followed by a blank line and then `<!-- HERO -->` — the top bar div appears to have been removed or left empty.
5. Acknowledgements section on the live page does NOT include "AQR Capital" or "The Idea Farm" which were in the original but removed during WSJ redesign. The current footer does reference Fama/French research papers and D3.js.
6. INSIGHTS.md documents the deleted insights.html — this is slightly confusing but harmless.

**Why:** Demo Day is 2026-05-14 (tomorrow). GitHub Pages deployment and Canvas URL submission are the only hard blockers for getting credit.

**How to apply:** When reviewing, prioritize GitHub Pages deployment confirmation and Canvas submission. All content and code quality issues are polish, not blockers.
