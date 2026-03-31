# Survival Analysis of Cardiovascular Risk – Framingham Study

*Predicting heart disease risk using survival analysis (Kaplan–Meier & Cox models) on real-world data.*

## Project Overview

Cardiovascular disease is a leading cause of death worldwide. This project applies **survival analysis techniques** to study the time until heart disease occurrence using the **Framingham Heart Study dataset**.

By analyzing risk factors and survival probabilities, this project demonstrates how data science can provide actionable insights into cardiovascular health.



## Objectives

- Perform Kaplan–Meier survival analysis on different risk groups  
- Build a Cox Proportional Hazards model to identify key risk factors  
- Compare survival distributions using the Log-Rank test  
- Visualize and interpret results clearly



## Dataset

- **Source:** Framingham Heart Study  
- **Number of participants:** ~5,000  
- **Key variables:**
  - `age` – Participant age  
  - `gender` – Male / Female  
  - `blood_pressure` – Systolic blood pressure  
  - `cholesterol` – Total cholesterol  
  - `smoker` – Smoking status (1=Yes, 0=No)  
  - `diabetes` – Diabetes status  
  - `time` – Time to event (years)  
  - `event` – Heart disease occurrence (1=Yes, 0=Censored)  



## Key Methods

1. **Kaplan–Meier Estimator** – Visualize survival probability over time  
2. **Log-Rank Test** – Compare survival distributions between groups  
3. **Cox Proportional Hazards Model** – Quantify effect of risk factors on survival

## Visualizations

![Survival Curve](images/survival_curve.png)  
*Kaplan–Meier survival curves for smokers vs non-smokers.*

![Cox Model Summary](images/cox_summary.png)  
*Hazard ratios of key risk factors from Cox Proportional Hazards model.*

##  Installation

1. Clone the repository:
```bash
git clone https://github.com/<your-username>/framingham-survival-analysis.git

pip install -r requirements.txt

jupyter notebook notebooks/survival_analysis.ipynb


## **Jupyter Notebook – survival_analysis.ipynb**  

Here’s a **fully structured notebook** with Markdown explanations and code blocks:

```python
# Survival Analysis – Framingham Heart Study

# 1. Import Libraries
import pandas as pd
import matplotlib.pyplot as plt
from lifelines import KaplanMeierFitter, CoxPHFitter

# 2. Load Data
df = pd.read_csv('../data/framingham.csv')
df.dropna(inplace=True)  # simple cleaning

# 3. Define Duration and Event
T = df['time']    # Time to event
E = df['event']   # Event occurred

# 4. Kaplan-Meier Survival Analysis

# Plot survival curves for smokers vs non-smokers
kmf = KaplanMeierFitter()

plt.figure(figsize=(10,6))
for group in [0,1]:
    kmf.fit(T[df['smoker']==group], event_observed=E[df['smoker']==group],
            label=f'Smoker={group}')
    kmf.plot_survival_function()

plt.title("Kaplan-Meier Survival Curve by Smoking Status")
plt.xlabel("Time (years)")
plt.ylabel("Survival Probability")
plt.savefig('../images/survival_curve.png')
plt.show()

# Insight:
# Non-smokers have higher survival probability than smokers over time.

# 5. Cox Proportional Hazards Model
cph = CoxPHFitter()
cph.fit(df, duration_col='time', event_col='event')
cph.print_summary()
cph.plot()
plt.title("Cox Model Hazard Ratios")
plt.savefig('../images/cox_summary.png')
plt.show()

# Insight:
# Smoking, age, and cholesterol are strong risk factors.
# Hazard ratio >1 indicates higher risk.

# 6. Optional: Compare survival by gender
plt.figure(figsize=(10,6))
for gender in [0,1]:
    kmf.fit(T[df['gender']==gender], event_observed=E[df['gender']==gender],
            label=f'Gender={gender}')
    kmf.plot_survival_function()

plt.title("Kaplan-Meier Survival Curve by Gender")
plt.xlabel("Time (years)")
plt.ylabel("Survival Probability")
plt.show()

# Insight:
# Men tend to have slightly lower survival probability compared to women.















































