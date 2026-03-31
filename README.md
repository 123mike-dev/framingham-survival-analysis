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

## 🏗️ Project Structure
