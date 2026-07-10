# GRID/HEAT — Con Edison Resilience Console

**Capstone Project 2027 — Energy Infrastructure Vulnerability in New York City**
*Develop data-driven strategies to improve the resilience of critical Con Edison assets.*

An interactive, offline-capable dashboard that models where extreme heat is most likely
to threaten the reliability of NYC's electric grid — and what to do about it — built on
real public data plus a second view comparing grid vulnerability across Texas, California,
and New York.

## What it does

**NYC ZIP View**
- Live-syncs the NYC Department of Health's Heat Vulnerability Index for all 180 NYC ZIP
  codes (NYC Open Data, dataset `4mhf-duep`), with an offline-first fallback cached locally
  so the app still works without a connection
- Combines that real data with the known structural differences between Con Edison's
  underground *network* grids (high redundancy, concentrated in Manhattan/inner boroughs)
  and more overhead *radial* grids (outer boroughs) into a modeled **Grid Stress Index**
  per ZIP code
- Ranks the most heat-vulnerable zones on a borough-organized schematic map and generates
  specific resilience recommendations per zone — undergrounding, submersible fault
  interrupters, demand response / conservation voltage optimization, predictive maintenance
  — matched to that zone's actual risk profile

**State Comparison View**
- Compares Texas (ERCOT), California (CAISO), and New York (NYISO / Con Edison) across five
  hazard axes: extreme heat, winter cold, wildfire, storm/flood, and grid isolation
- Explains why grid *architecture* — not just weather — drives outcomes: ERCOT's isolation
  from the Eastern and Western Interconnections was central to Winter Storm Uri's 2021
  blackouts, while California's wildfire risk drives its Public Safety Power Shutoff program
- Includes a timeline of real, documented events (Winter Storm Uri, Hurricane Sandy,
  major PSPS shutoffs) with cited sources

Every number the model doesn't pull live is disclosed as an illustrative estimate — see the
**Methodology & data sources** panel at the bottom of each view in the app itself.

## Run it

Just open `index.html` in a browser — no build step, no dependencies to install.

Live: `https://jonathanodiadi168.github.io/capstone-project-2027/` (once GitHub Pages is enabled — see below)

## Deploy on GitHub Pages

1. **Settings → Pages**
2. Source: **Deploy from a branch**
3. Branch: **main**, folder: **/ (root)**
4. **Save**, then wait a minute or two for the first build

## Tech

Single-file architecture by design: plain JavaScript (no frameworks), [W3.CSS](https://www.w3schools.com/w3css/)
for layout, [Chart.js](https://www.chartjs.org/) for visualizations, and IndexedDB for
offline-first local caching. A cloud-sync extension point (`syncToCloud`) is stubbed in for
a future DynamoDB-backed backend.

## Data sources

- NYC DOHMH — Heat Vulnerability Index Rankings ([NYC Open Data](https://data.cityofnewyork.us), dataset `4mhf-duep`)
- Con Edison — Electric Grids 101 / Electric System Overview; 2024 Sustainability Report
- FERC — Final Report on the February 2021 Cold Weather Event
- CPUC / CAISO — Public Safety Power Shutoff program fact sheets; PG&E SEC filings
