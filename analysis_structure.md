# Analysis Workflow Overview

This repository contains a complete, reproducible workflow for performing survival analysis on clinical trial data.  
The script is organized into **10 logical modules**, each representing a key stage in the analytical pipeline.

---

## 1. Imports & Configuration
Loads all required Python libraries (`lifelines`, `pandas`, `matplotlib`) and defines:

- The input data path  
- The list of clinical outcome variables (`analysis_vars`) such as **TLC**, **CPIS**, and **Culture**

---

## 2. Helper Functions
Utility functions used throughout the workflow:

- **`calculate_duration`** – Computes the last day with a valid measurement for a given variable  
- **`pick_column`** – Selects the first available column from a list of candidate names  
- **`safe_fit_cox`** – Fits a CoxPH model with error handling

---

## 3. Data Loading
Reads the primary dataset:  
**`Data form Chlorhexidine Trial.xlsx`**  
into a pandas DataFrame.

---

## 4. Preprocessing
The function **`prepare_analysis_df`** constructs essential survival-analysis variables:

- **Duration** — time to event or censoring  
- **Event** — 1 for death, 0 otherwise (`Outcome of current episode 2`)

These variables are used by Kaplan–Meier and CoxPH models.

---

## 5. Kaplan–Meier Plotting
Two functions provide unadjusted survival visualization:

- **`plot_km_overall`** – Overall Kaplan–Meier survival curve  
- **`plot_km_by_arm`** – Survival curves stratified by trial arm

---

## 6. Log-Rank Test
**`do_logrank`** performs the log-rank test to compare survival distributions between the trial arms.

---

## 7. CoxPH Modeling & Summary
Multivariable survival analysis is performed using:

- **`prepare_cox_inputs`**  
  - Mean imputation for APACHE II Score  
  - Binary encoding for *Trial Arm* and *Gender*

- **`show_cox_plots_and_summary`**  
  - Fits the CoxPH model  
  - Outputs HRs, confidence intervals, and p-values  
  - Produces a forest plot of adjusted hazard ratios

- **`show_partial_effects`**  
  - Generates adjusted survival curves for Age, Gender, and Trial Arm

---

## 8. Proportional Hazards Assumption Check
**`show_ph_assumption_plots`** runs `cph.check_assumptions` and produces diagnostic plots verifying the proportional hazards assumption.

---

## 9. Main Execution Loop
Iterates through all outcomes listed in `analysis_vars`, performing:

- Kaplan–Meier analysis  
- Log-rank test  
- CoxPH modeling  

for each clinical endpoint.

---

## 10. Wrap-Up
Completes execution after processing all outcome variables.

---

# Clinical Endpoints Analyzed

Survival duration is evaluated for the following outcomes:

- Total Leukocyte Count (**TLC**)  
- Band Form  
- Chest X-ray  
- Clinical Pulmonary Infection Score (**CPIS**)  
- Arterial Blood Gas (**ABG**)  
- Culture  
- OS Microbial Load  
- Ulcer

---
