# Chlorhexidine-Trial-Survival-Analysis---Python
The analysis investigates patient survival duration based on the time-to-occurrence of various clinical endpoints, comparing outcomes between different patient arms and adjusting for covariates.

Chlorhexidine Survival Analysis: Trial Outcome Prediction
This repository contains Python code for performing a survival analysis on data from a Chlorhexidine trial. The primary goal is to assess patient survival duration based on various clinical events and to investigate the effect of the Trial Arm (intervention) using established survival modeling techniques, including the Kaplan-Meier estimator and the Cox Proportional Hazards (CoxPH) model.


Key Objectives:
Calculate Survival Duration: Determine the duration a patient is observed based on different clinical endpoints (e.g., TLC, CPIS, Culture).

Estimate Overall Survival: Use the Kaplan-Meier Fitter to estimate and visualize the overall survival probability. 3. Compare Trial Arms: Compare survival curves between the different trial arms using the Kaplan-Meier estimator and a formal Log-Rank Test.

Model Hazard Ratios: Fit a multivariate CoxPH model to calculate adjusted Hazard Ratios (HRs) for the Trial Arm, Age, APACHE II Score, and Gender, controlling for potential confounders.

Check Model Assumptions: Assess the validity of the CoxPH model by checking the Proportional Hazards (PH) assumption.
