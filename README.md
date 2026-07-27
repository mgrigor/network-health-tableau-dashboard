# Network Health — LTE Vendor Performance & Anomaly Detection Dashboard

An interactive Tableau dashboard for monitoring multi-vendor LTE network performance and surfacing degrading or anomalous sites — modeled after the kind of monthly vendor-performance reporting I build in my current role as a network analytics engineer.

**Live dashboards on Tableau Public:**
- [Vendor Comparison Dashboard →](https://public.tableau.com/app/profile/marthony.rigor/viz/Network_Health/VendorComparisonDashboard)
- [Worst Cell / Anomaly Heatmap →](https://public.tableau.com/app/profile/marthony.rigor/viz/Network_Health/WorstCellAnomalyHeatmap_1)

---

## Overview

This project tracks three core LTE success-rate KPIs — S1, RRC, and Initial ERAB Establishment — across three network equipment vendors (Ericsson, Nokia, Samsung), then layers in anomaly detection to flag which sites are degrading over time versus experiencing one-off spikes.

It's built to answer two questions network engineering teams ask every month:
1. **How is each vendor performing** on our core success-rate KPIs?
2. **Which specific sites need attention** — are they trending worse over time, or did something just spike once?

## Dataset

The dataset is **synthetic**, generated to reflect the structure, scale, and patterns of real multi-vendor LTE performance data — including planted degrading-site trends and injected anomaly spikes so the anomaly-detection logic has something real to catch. No production or customer data is included.

## Dashboards

### 1. Vendor Comparison Dashboard
Side-by-side comparison of S1, RRC, and Initial ERAB Establishment success rates by vendor, with exact values labeled on each bar for quick reading.

![Vendor Comparison Dashboard](screenshots/vendor_comparison_dashboard.png)

### 2. Worst Cell / Anomaly Heatmap
A site-by-day heatmap (sorted worst-to-best by average failure rate) that visually distinguishes two failure patterns:
- **Gradual degradation** — a site darkening steadily over its date range
- **Isolated anomalies** — a single dark spike surrounded by otherwise normal readings

![Worst Cell / Anomaly Heatmap](screenshots/worst_cell_anomaly_heatmap.png)

### 3. Worst Cell — Flagged Status
A binary view of the same data, applying a fixed failure-rate threshold to classify each day as **Normal** or **Flagged**. This makes it easy to see, at a glance, which sites cross into sustained flagged status (likely degrading) versus a brief flagged blip that recovers (likely a one-off anomaly).

![Worst Cell — Flagged Status](screenshots/worst_cell_flagged_status.png)

## Key Findings (from the synthetic dataset)

- **Sustained degradation:** DAL_016, CHI_018, DAL_022, NEW_025, NEW_019, and NEW_009 all show a clear worsening trend over the observation window, crossing into "Flagged" status and remaining there.
- **Isolated anomalies:** NEW_004, CHI_021, NEW_013, and CHI_012 show brief spikes that return to normal — consistent with one-off events rather than systemic issues.
- Across all three vendors, success rates stayed within a fairly tight band (~98.8%–99.7%), with Samsung and Ericsson consistently edging out Nokia on RRC and Initial ERAB Establishment success rates.

## Tools & Techniques

- **Tableau** — dashboard design, heatmap visualization, calculated fields, dashboard actions
- **Data modeling** — site/vendor/market dimensional structure
- **Python** — synthetic dataset generation

## Files

- `Network_Health.twbx` — packaged Tableau workbook (includes bundled data)
- `synthetic_lte_kpi_dataset.csv` — source dataset
- `screenshots/` — static previews of each dashboard

## About This Project

This dashboard mirrors work I do monthly in my current role monitoring multi-vendor LTE network performance — built here on a synthetic dataset to make it shareable as a public portfolio piece.

**Marthony Rigor** | [LinkedIn](https://linkedin.com/in/marthony-rigor-b1714758) | [GitHub](https://github.com/mgrigor)
