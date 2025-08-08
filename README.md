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
1. **Understand menstrual cycle patterns**  
   - Distribution of cycle length & duration  
   - Seasonal/yearly trends  
   - Missing cycle detection & imputation  

2. **Explore weight data**  
   - Long-term weight trends  
   - Missing data visualization & interpolation  
   - Seasonal/weekday/monthly effects  

3. **Link menstrual and weight data**  
   - Weight changes before and after **Period Start** and **Ovulation**  
   - Statistical tests for significance (t-test, ±7 days)  

4. **Discover patterns with clustering**  
   - Group similar weight change curves across cycles using K-means  
   - Compare clusters by cycle length, season, year, and duration  

---

## 4. Analysis Workflow
### Step 1 — Data Cleaning
- Parse XML & Excel into DataFrames
- Detect missing periods (>48 days between starts)
- Impute missing cycles using average of surrounding cycle lengths
- Derive:
  - `cycle_length`
  - `duration_days`
  - `ovulation_date`
  - `season`, `year`

### Step 2 — Individual Analyses
**Menstrual data**:
- Trends over time  
- Histograms & seasonal breakdowns  
- Missing period detection & visualization  

**Weight data**:
- Moving averages for long-term trends  
- Seasonal analysis (month, quarter, year)  
- Heatmaps of missing vs recorded days  

### Step 3 — Combined Analysis
- Align weight to:
  - **Period Start**
  - **Ovulation**
- Calculate before vs after mean weights  
- Apply t-test for statistical significance  
- Visualize:
  - Multiple cycle curves (thin gray lines)
  - Average trend (bold red line)
  - Vertical dashed event markers

### Step 4 — Pattern Discovery
- Normalize each cycle’s weight curve (z-score)
- Use **K-means clustering** to group patterns
- Evaluate K using silhouette score
- Compare clusters:
  - Cycle length
  - Duration
  - Season
  - Year

---

## 5. Key Findings
- Slight **weight increase before period start** (p ≈ 0.02, ±7 days)
- No statistically significant weight change around ovulation
- Two distinct weight change pattern clusters:
  - **Cluster 0**: Shorter cycles (~27 days), slightly longer duration  
  - **Cluster 1**: Longer cycles (~31 days), different seasonal distribution

---

## 6. Repository Structure
 ```
├── data/
│ ├── period.xml # Original menstrual cycle data
│ ├── weight.xlsx # Original weight data
│ ├── period_clean.csv # Cleaned & enriched menstrual data
│ ├── weight_clean.csv # Cleaned weight data
│ └── merged_data.csv # Combined dataset for joint analysis
├── notebooks/
│ ├── 01_period_analysis.ipynb # Menstrual cycle analysis
│ ├── 02_weight_analysis.ipynb # Weight data analysis
│ ├── 03_weight_vs_period.ipynb # Combined event-based analysis
│ ├── 04_clustering_patterns.ipynb # Pattern discovery via clustering
├── requirements.txt
└── README.md

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
