# Personal Health Data Analysis: Weight & Menstrual Cycles

## 1. Overview
This project analyzes **personal menstrual cycle** and **daily weight tracking** data to uncover:
- Long-term trends
- Seasonal patterns
- Relationships between weight changes and menstrual events

The dataset spans **2015–2025** and is self-recorded.  
It serves as a personal health analytics case study and a demonstration of time series + event-based analysis techniques.

---

## 2. Data Sources
- **`data/period.xml`** – Menstrual cycle data (exported from a tracking app)  
  Includes:
  - Start and end dates for each cycle
  - Cycle duration
- **`data/weight.xlsx`** – Daily weight records

---

## 3. Goals
1. **Menstrual cycle analysis**  
   - Cycle length & duration distribution
   - Seasonal/yearly trends
   - Detect & impute missing cycles
2. **Weight analysis**  
   - Long-term trends & seasonal effects
   - Missing data heatmaps
3. **Combined analysis**  
   - Weight change before/after **Period Start** & **Ovulation**
   - Statistical significance (t-test)
4. **Pattern discovery**  
   - K-means clustering of normalized weight curves
   - Cluster comparison by cycle length, season, year


---

## 4. Analysis Workflow
### Step 1 — Data Cleaning
- Parse XML & Excel → DataFrames
- Detect missing cycles (>48 days gap)
- Impute missing using average length
- Derive `cycle_length`, `duration_days`, `ovulation_date`, `season`, `year`

### Step 2 — Separate Analyses
- **Menstrual data**: trends, histograms, seasonal breakdown  
- **Weight data**: moving averages, seasonal trends, missing data heatmaps

### Step 3 — Event-based Analysis
- Align weight to:
  - Period Start
  - Ovulation
- Compare before vs after (±7 days)
- Paired t-test for significance
- Plot individual cycles + average

### Step 4 — Clustering
- Z-score normalize each cycle's weight curve
- K-means clustering
- Choose K via silhouette score
- Compare clusters by cycle metrics & seasonal/annual distribution

---

## 5. Key Findings
- **Weight increase before period start**: +0.16 kg, p ≈ 0.02 (±7 days)
- No significant change around ovulation
- **Two main clusters**:
  - **Cluster 0**: Shorter cycles (~27 days), sharper pre-period increase  
  - **Cluster 1**: Longer cycles (~31 days), flatter/decreasing trend

---

## 6. Repository Structure
 ```
data/
├── period.xml # Original menstrual data
├── weight.xlsx # Original weight data
├── period_clean.csv # Cleaned menstrual data
├── weight_clean.csv # Cleaned weight data
notebooks/
├── 01_period_analysis.ipynb # Menstrual cycle analysis
├── 02_weight_analysis.ipynb # Weight analysis
├── 03_weight_vs_period.ipynb # Event-based analysis
├── 04_clustering_patterns.ipynb # K-means clustering
requirements.txt
README.md
 ```

---

## 7. How to Run
```bash
# Install dependencies
pip install -r requirements.txt

# Start Jupyter
jupyter notebook
 ```

---

## 8. Dependencies
- pandas
- numpy
- matplotlib
- seaborn
- plotly
- scikit-learn
- ruptures

---

## 9. License
This project contains personal health data.
The included datasets are anonymized and provided for educational and research purposes only.
Not intended for medical diagnosis or advice.

