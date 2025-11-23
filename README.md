# STAT 403 Final Project — Bootstrapping Regression & Jackknife+ Conformal Prediction

This repository contains my final project for **STAT/QSci 403: Introduction to Statistical Methods for Data Science** at the University of Washington (Spring 2025).  
The project focuses on regression modeling, uncertainty quantification, and distribution-free prediction using modern resampling methods.

---

## 📌 Project Overview

The goal of the analysis is to model **log10-transformed house prices** in King County (Seattle area) using features such as:

- square footage (`sqft_living`)
- number of bathrooms and bedrooms
- house grade  
- log-transformed predictors to improve linearity and reduce heteroscedasticity

The project includes:

1. **Linear regression modeling**
2. **Gaussian confidence intervals**
3. **Bootstrap confidence intervals**
4. **Jackknife+ conformal prediction intervals**
5. **Uncertainty quantification and empirical coverage assessment**

All results are implemented in **R**, and code is available in the project files.

---

## 📈 Regression Modeling

I fit the model:

$\log_{10}(\text{price}) 
= \beta_0 
+ \beta_1 \log_{10}(\text{sqft\_living})
+ \beta_2 \text{bedrooms}
+ \beta_3 \text{bathrooms}
+ \beta_4 \text{grade}
+ \varepsilon$

Key findings:

- `log_sqft` and `grade` are **highly significant predictors**  
- Bedrooms and bathrooms show **weak marginal effects** once other variables are controlled
- Adjusted R² ≈ **0.556**, indicating moderate explanatory power

(Visuals available in the PDF report.)

---

## 🔁 Bootstrap Confidence Intervals

I computed **95% bootstrap CIs** for all coefficients using 1,000 bootstrap resamples.

Example (log_sqft):

- Gaussian CI: **(0.23, 0.54)**
- Bootstrap CI: **(0.23, 0.55)**  
- Both methods confirm the robustness of this predictor.

Histograms of bootstrap estimates for each coefficient are shown in the report (see page 5).

---

## 🔮 Jackknife+ Conformal Prediction

To produce **distribution-free prediction intervals**, I implemented **Jackknife+**:

- 500 leave-one-out models
- 200 test-set predictions per model
- Constructed (Li, Ui) bounds from residuals
- Exponentiated back to the price scale

### Empirical coverage:

- **196 out of 200 test cases (98%)**  
- Exceeds the target **95%** coverage

### Interval widths:

- Median width: **\$840,652**
- Range: **\$286k – \$3.39M**

(First 20 prediction intervals plotted in the report, page 6.)

---

## 📁 File Structure

- 403_final_report.pdf # Full project write-up
- code/ # R scripts for regression, bootstrap, Jackknife+
- data/ # Training and test datasets
- CI.dat # Jackknife+ interval outputs
- guess.dat # Test-set MSE and coverage summary
- README.md # This file


---

## 🧠 Methods Used

- Linear regression
- Gaussian confidence intervals
- Bootstrap resampling (percentile & BCa)
- Jackknife+ conformal prediction
- Diagnostic plots & residual analysis

---

## ✨ Highlights

- Demonstrates **statistical rigor** beyond simple modeling  
- Shows understanding of **model assumptions and violations**
- Uses **modern distribution-free prediction methods**
- Connects theory with applied predictive modeling

This project represents my interest in **statistical learning**, uncertainty quantification, and methods that remain reliable in noisy real-world settings—topics I hope to further explore in the **ETH Zürich MSc in Data Science** program.

---
