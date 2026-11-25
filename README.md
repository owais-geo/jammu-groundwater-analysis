# Spatio-Temporal Groundwater Level & Monsoon Recharge Analysis — Jammu District (J&K)

An exploratory hydrogeological analysis of groundwater depth, seasonal fluctuation, and aquifer recharge across **Jammu District, Jammu & Kashmir**, built in Python using open monitoring records from the **Central Ground Water Board (CGWB)** via the National Water Data Portal (NWDP).

## Key Findings (2021–2023)

| Metric | Value |
|---|---|
| **Monitoring Stations Analysed** | 122 stations |
| **Cleaned Quarterly Observations** | 777 readings |
| **Temporal Coverage** | 2021 – 2023 |
| **Median Depth to Water Table** | 3.30 m bgl |
| **Observed Depth Range** | 0.06 m bgl (shallowest) to 38.46 m bgl (deepest) |
| **Median Monsoon Water-Table Rise (May to Nov)** | +1.46 m |

### Hydrogeological Interpretation
* **Kandi–Sirowal–Alluvial Transition:** The nearly 38-metre depth spread across a single district reflects the physical transition from the coarse, boulder-pebble piedmont zone (**Kandi belt**, northern Jammu) with deep water tables to the fine-grained **Sirowal and southern alluvial plains**, where groundwater sits within a few metres of the surface.
* **Monsoon Recharge Dominance:** Paired pre-monsoon (May) and post-monsoon (November) measurements confirm a median water-table recovery of **+1.46 m**, highlighting the aquifer network's strong dependence on southwest monsoon precipitation.

---

## Visual Outputs

### 1. Seasonal Water-Table Depth & Monsoon Recharge

![Seasonal groundwater depth and monsoon rise in Jammu](figures/fig1_seasonal_water_level_jammu.png)

### 2. Spatial Gradient of Groundwater Depth

![Spatial gradient of groundwater depth across Jammu District](figures/fig3_spatial_depth_jammu.png)

### 3. Interactive Station Map

Explore station-wise mean depth to water table interactively:

[Open Interactive Jammu Groundwater Map](jammu_groundwater_map.html)

## Methodology & Data QA Pipeline

1. **Automated Schema Standardisation:** Dynamic column matching and date parsing (`dayfirst=True`) to handle irregular government portal headers.
2. **Quality Control & Deduplication:** Removed missing timestamps and implausible depth records, and collapsed same-day repeat station measurements by taking daily means per `(station, date)`.
3. **Seasonal Classification:** Grouped CGWB quarterly rounds into Winter (Jan), Pre-Monsoon (May), Monsoon (Aug), and Post-Monsoon (Nov).
4. **Recharge Calculation:** Computed paired station-year seasonal recovery as:
   $$\Delta h = \text{Depth}_{\text{Pre-Monsoon}} - \text{Depth}_{\text{Post-Monsoon}}$$
   where positive values indicate post-monsoon water-table rise.

---

## Repository Structure

```text
jammu-groundwater-analysis/
├── 01_jammu_groundwater_analysis.ipynb   # End-to-end Google Colab analysis notebook
├── outputs/
│   ├── data/
│   │   └── jammu_gwl_clean.csv           # Cleaned Jammu district station dataset
│   ├── figures/
│   │   ├── fig1_seasonal_water_level_jammu.png
│   │   └── fig3_spatial_depth_jammu.png
│   └── jammu_groundwater_map.html        # Interactive Folium station map
├── requirements.txt
└── README.md
