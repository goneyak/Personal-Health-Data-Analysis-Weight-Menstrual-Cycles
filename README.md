# 📊 Personal Health Data Analysis: Weight & Menstrual Cycles

## 1. Overview
This project analyzes **personal menstrual cycle** and **weight tracking** data to uncover trends, seasonal patterns, and relationships between the two.  
The dataset spans from **2015 to 2025** and is self-recorded.

## 2. Data Sources
- **`data/period.xml`** – Original menstruation tracking data (exported from app).
- **`data/weight.xlsx`** – Daily weight records.

## 3. Goals
1. **Understand menstrual cycle patterns**  
   - Cycle length distribution, seasonal trends, yearly changes.
2. **Explore weight trends**  
   - Long-term trends, seasonality, weekday/month effects.
3. **Link the two datasets**  
   - Analyze weight changes around period start & ovulation.
4. **Pattern discovery**  
   - Cluster similar weight change patterns across cycles.

## 4. Analysis Steps
### Step 1 — Data Cleaning
- Parse XML & Excel to pandas DataFrame.
- Detect missing periods using a **48-day threshold**.
- Impute missing cycles using average cycle length.
- Derive:
  - `cycle_length`
  - `duration_days`
  - `ovulation_date`
  - `season`, `year`

### Step 2 — Individual Analysis
- **Period data**: Trends, histograms, seasonal breakdown.
- **Weight data**: Trendlines, moving averages, seasonality.

### Step 3 — Combined Analysis
- Align weight data around:
  - **Period Start**
  - **Ovulation**
- Compare **before vs after mean weights** (t-test, ±7 days).
- Visualize individual cycles & average trends.

### Step 4 — Clustering
- Z-score normalization of each cycle’s weight curve.
- **K-means clustering** to group similar patterns.
- Compare clusters by:
  - Cycle length
  - Season
  - Year
  - Menstruation duration

## 5. Key Findings
- Slight weight increase before period start (**p ~ 0.02** over ±7 days).
- No statistically significant weight change around ovulation.
- Two main pattern clusters:
  - **Cluster 0**: Shorter cycles (~27 days), slightly longer durations.
  - **Cluster 1**: Longer cycles (~31 days), different seasonal distribution.

## 6. Repository Structure
├── data/
│ ├── period.xml
│ ├── weight.xlsx
│ ├── period_clean.csv
│ ├── weight_clean.csv
│ └── merged_data.csv
├── notebooks/
│ ├── 01_period_analysis.ipynb
│ ├── 02_weight_analysis.ipynb
│ ├── 03_weight_vs_period.ipynb
│ ├── 04_clustering_patterns.ipynb
└── README.md
