# From a Crop's Environmental Fingerprint to Global Yield Trends
### AVCAD final project (2372 — Analysis and Visualization of Complex Agro-Environmental Data), GreenDS MSc, ISA/ULisboa 2025/2026

**Authors:** Aster Noel Dsouza (29211) · David Heleno Bebiano da Costa Morais (29400)

A coherent exploratory, inferential and multivariate analysis of Smart-Farming agro-environmental
data, from the individual plot to the planet. Companion to our Applied Machine Learning (2373)
study — same theme and data, independent analyses.

## Repository layout
```
final_project/
├── README.md
├── final_project_code_annex.ipynb     # the code annex — reproduces every figure & statistic
├── requirements.txt
├── data/                               # the three datasets
│   ├── Crop_recommendation.csv
│   ├── oecd_crop_production.csv
│   └── crop_yield_sample.csv
├── figures/                            # 14 figures used in the report (PNG)
├── report/                             # the written report (main deliverable)
│   ├── AVCAD_Final_Project_Report.docx
│   └── AVCAD_Final_Project_Report.pdf
└── dashboard/
    └── AVCAD_dashboard.html            # interactive Plotly dashboard (open in a browser)
```

## The three datasets
1. **Crop Recommendation** (Kaggle, 2,200×7, 22 crops) — core multivariate analysis.
2. **OECD/FAO crop production** (48 countries, 1990–2025, 4 crops) — real geographical & temporal trends.
3. **Crop Yield** (Kaggle, synthetic) — supporting categorical hypothesis tests.

## How to reproduce (Google Colab)
1. In a Colab cell, clone the repo so the data is on disk:
   ```python
   !git clone https://github.com/asternoeld/avcad
   ```
   The notebook reads from `avcad/final_project/data`.
2. Open `final_project_code_annex.ipynb` → **Runtime → Run all**.

Locally instead: `pip install -r requirements.txt` and run the notebook with the CSVs in `data/`.

## Crop grouping
The 22 crops are mapped to four agronomic groups for the comparative analyses:
**Cereals** (rice, maize) · **Pulses** (chickpea, kidneybeans, pigeonpeas, mothbeans, mungbean,
blackgram, lentil) · **Fruits** (banana, mango, grapes, watermelon, muskmelon, apple, orange,
papaya, coconut, pomegranate) · **Commercial** (cotton, jute, coffee).

## Headline findings
- Crop groups occupy **statistically distinct** soil–climate envelopes (ANOVA/Kruskal p < 0.001 for every variable; humidity, nitrogen and rainfall separate them most).
- The environmental space is **multidimensional** (3 PCs for ~62% variance); **LDA** separates groups at **85%** accuracy; "cereals" is the least coherent group (rice ≠ maize environmentally).
- **Clustering** only partly matches the agronomic groups (Adjusted Rand Index ≈ 0.34) — environmental niche cuts across taxonomy.
- In the **synthetic** yield data only management variables (irrigation/fertiliser) carry signal — a clean external-validity caution.
- **Real** OECD yields rose significantly 1990–2025 (maize +0.77 t/ha per decade) with a significant geographical gap (Oceania/Americas high, Africa low).

## Relationship to the ML (2373) project
Same datasets and Smart-Farming theme; analyses are independent. ML = supervised prediction
(classification/regression, SHAP, climate stress-test). AVCAD = descriptive/inferential/unsupervised
(EDA, hypothesis tests, PCA/LDA/clustering, geo-temporal visualisation). No ML model is reused here.
