---
title: "Applying Application Credit Scoring to B2B2C Models in Vietnam"
collection: projects
type: "Credit scoring"
permalink: /projects/2012-03-01-Ascore-B2B2C
date: 2023-12-20

authors: "Trang Do"
venue: 'Personal Project'
image: "/images/projects/image_ascore1.png"

project_page: /projects/2012-03-01-Ascore-B2B2C
paper: "#"
---

## Overview

Developed a credit scoring model for Ascore to predict customer default risk within a defined time horizon.

The project follows an end-to-end scorecard development pipeline, including target definition, data preprocessing, model development, score scaling, and calibration. The model supports more reliable risk assessment and enables data-driven credit decision-making.

---

## Key Results
* Gini: 55% (train), 50% (test), 51% (validation)
* Reduced default rate from ~30% → 15% (cut-off strategy)
* Improved portfolio profitability: -11.6% → 15%

---

## Business Problem

Accurate credit risk assessment is essential for financial institutions to manage portfolio risk and maintain sustainable growth. However, predicting customer default remains challenging due to data quality issues and changing customer behavior over time.

This project aims to develop a robust credit scoring model for Ascore that can reliably estimate default probability, enabling:

* Better identification of high-risk customers
* More consistent credit decision-making
* Improved risk management across the portfolio

---

## Data
![Sample distribution and default rate]({{ "/images/projects/ascore_sample_sum.JPG" | relative_url }})

The dataset consists of real-world lending data collected from a B2B2C payment platform in Vietnam (01/2022 - 03/2023), totaling approximately **14K records**, with an overall default rate of ~30%.  

The data includes customers who:
- Submitted applications  
- Were approved through internal credit review processes  
- Initiated at least one order within 3 months of application  

An additional **out-of-time (OOT) dataset** covering **April 2023 – July 2023** is used for model validation.  

The dataset is split into:
- Train/Test: 70/30  
- Separate OOT dataset for temporal validation

---

## Target Definition

- Default (1): DPD > 60 at 9 months after first transaction  
- Non-default (0): DPD ≤ 60  

Scope:
- Approved customers with at least one transaction within 3 months  

Default threshold (DPD 60+) is selected based on roll rate analysis, while a 9-month performance window is chosen using vintage analysis.

---

## Feature Engineering & Selection

![Long-list variables]({{ "/images/projects/ascore_longlist_chart.png" | relative_url }})

From 81 variables, a structured selection process was applied:

* Remove variables with >40% missing values
* Remove highly correlated variables (>80%)
* Apply WOE transformation
* Filter variables using IV (IV ≥ 0.05)
* Apply stepwise selection

This ensures a balance between predictive power, interpretability, and stability.

---

## Model Development

A logistic regression model was selected for scorecard development due to its strong interpretability and proven effectiveness in credit risk modeling.  

While more advanced models (e.g., gradient boosting, neural networks) can offer higher predictive power, logistic regression provides:
- Transparent feature impact (critical for risk interpretation)  
- Stable performance on structured financial data  
- Easy conversion into scorecard format for business use  

The model estimates probability of default (PD), which is subsequently scaled and calibrated into a credit score for practical deployment.

---

## Scorecard Scaling
![Score range after scaling]({{ "/images/projects/ascore_scaling_pd_range.png" | relative_url }})

Model outputs (probability of default) are transformed into a standardized credit score using a linear scaling approach.  

- Score range: 0–850  
- Higher score indicates lower credit risk  
- PDO (points to double the odds): 40  

A reference point is defined such that a score of **540 corresponds to ~33% default probability**, ensuring alignment between score and underlying risk.  

This scaling framework allows:
- Clear interpretation of risk changes  
- Additive score contributions from features  
- Practical use in credit decision systems (cut-off, segmentation, pricing)

---

## Model Result
<div style="display: grid; grid-template-columns: repeat(3, 1fr); gap: 12px; margin: 20px 0;">
  <img src="{{ '/images/projects/ascore_roc_train.png' | relative_url }}" style="width: 100%; height: 180px; object-fit: cover;">
  <img src="{{ '/images/projects/ascore_roc_test.png' | relative_url }}" style="width: 100%; height: 180px; object-fit: cover;">
  <img src="{{ '/images/projects/ascore_roc_validation.png' | relative_url }}" style="width: 100%; height: 180px; object-fit: cover;">
</div>

**Discrimination (Gini):**

* Gini > 80% across train, test, and validation

**Stability (PSI):**

* PSI < 0.03 → strong stability

---

## Business Impact

**Risk segmentation:**

* Reduced default rate from ~10% → 2.4%

**Credit policy optimization:**

* Increased limits for low-risk segments
* Reduced exposure for high-risk customers

**Risk-based pricing:**

* Flat rate → segmented pricing strategy
* Profit improvement: 7.9% → 10%

---

## Links

* Project page: *(add deployed link)*

---

