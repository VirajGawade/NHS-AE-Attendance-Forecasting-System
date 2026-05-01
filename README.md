# NHS A&E Attendance Forecasting System

## 🎓 MSc Dissertation — Queen Mary University of London, 2025
**Supervisor: Alireza Sanaee | Programme: MSc Big Data Science**

An end-to-end, production-ready forecasting system for predicting 
NHS Accident & Emergency attendance across all 7 NHS England regions, 
using a hybrid LSTM + Machine Learning approach with SHAP 
explainability — deployed as an interactive Streamlit dashboard.

**Tech Stack:** Python · TensorFlow/Keras · Scikit-learn · XGBoost · 
Pandas · NumPy · SHAP · Streamlit · Google Trends API · 
Met Office Data · NHS Open Data

---

## The Problem

Over 3,500 urgent 999 calls go unanswered daily in England because 
ambulances are delayed outside hospitals. Only 123 of 930+ NHS 
hospitals have access to AI forecasting tools. The remaining hospitals 
rely on basic Excel-based tools that cannot predict demand.

This project builds a free, open, interpretable forecasting system 
accessible to any NHS hospital.

---

## What This System Does

- Predicts A&E attendance at **monthly, weekly, and 7-day daily** 
  granularities
- Forecasts separately for all **7 NHS England regions**
- Combines LSTM and ML predictions via a **hybrid weighted model**
- Explains predictions using **SHAP** (SHapley Additive Explanations)
- Deploys via **interactive Streamlit dashboard** — no coding needed

---

## Results

| Granularity | Best MAPE | All Regions Accuracy |
|-------------|-----------|----------------------|
| Monthly | 0.43% (South East) | > 93% across all regions |
| Weekly | ~1.6% (London) | > 90% across all regions |
| Daily | Weighted proxy | Regional hybrid model |

Monthly LSTM: MAPE below 6.2% across all 7 NHS regions.
<img width="600" height="500" alt="forecast_plot_London_hybrid_monthly_2025-05" src="https://github.com/user-attachments/assets/ecbcc6a9-d875-4ba4-9e86-ddff7b61516f" />
---

## Data Sources (8 Sources Integrated)

| Source | Data |
|--------|------|
| NHS England A&E Statistics | Attendance & performance data |
| NHS ECDS | Emergency care demographics |
| UKHSA Surveillance | Flu, COVID, respiratory trends |
| UK Met Office | Temperature, rainfall, weather |
| ONS Nomis | Population by age, gender, region |
| Fingertips PHE | Deprivation, smoking, alcohol indicators |
| NEL Growth Files | Non-elective admission growth rates |
| Google Trends | Search behaviour (A&E near me, ambulance) |

---

## Models

| Model | Type | Use |
|-------|------|-----|
| LSTM | Deep Learning | Long-term temporal patterns |
| Random Forest | ML Ensemble | Short-term feature-based |
| XGBoost | ML Ensemble | Short-term feature-based |
| Hybrid | Combined | 70% ML + 30% LSTM weighted |

**Hybrid Formula:**
Hybrid = 0.7 × ML + 0.3 × LSTM

---

## SHAP Explainability

ML models are explained using SHAP — showing which features 
drive predictions up or down. Key influential features include:
- Other_Attendances (lagged)
- Type1_Attendances (lagged)
- Hospital waiting times
- NEL_YTD_Growth
- Google Trends: "A&E near me"
- Emergency_Admissions

This makes the system transparent for non-technical NHS decision 
makers — unlike commercial black-box tools.

---

## System Architecture

**Pipeline:**
1. Data collection (8 sources, April 2019 – May 2025)
2. Data cleaning & regional alignment (20 → 7 NHS regions)
3. Monthly → Weekly conversion using Google Trends weights
4. Feature engineering (lag features, rolling stats, seasonal flags)
5. LSTM + ML model training (per region, per granularity)
6. Hybrid prediction generation
7. SHAP explainability plots
8. Streamlit dashboard deployment

---

## How to Run

1. Clone the repo
git clone https://github.com/VirajGawade/nhs-regional-forecast

2. Install requirements
pip install -r requirements.txt

3. Launch the Streamlit dashboard
streamlit run streamlit_app.py

4. In the dashboard:
- Select region (e.g. London, Midlands)
- Select model (Hybrid / LSTM / ML)
- Select granularity (Monthly / Weekly / Daily)
- Select date
- Click Run — view forecast + SHAP explanation

---

## Repository Structure

| File/Folder | Description |
|-------------|-------------|
| streamlit_app.py | Main dashboard app |
| Regional_LSTM_*.py | LSTM training scripts |
| Regional_ML_*.py | ML training scripts |
| Hybrid_*.py | Hybrid prediction scripts |
| regional_engineered_features.py | Feature engineering |
| shap_explain.py | SHAP explainability |
| cleaned datasets/ | Preprocessed NHS data |
| requirements.txt | Python dependencies |

---

## Author

**Viraj Gawade**
MSc Big Data Science — Queen Mary University of London, 2025
linkedin.com/in/viraj-gawade-b7b346262 | 
github.com/VirajGawade
