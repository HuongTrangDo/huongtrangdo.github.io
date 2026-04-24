---
title: "Applying Behavioral Credit Scoring to B2B2C Models in Vietnam"
collection: projects
type: "Credit scoring"
permalink: /projects/2012-03-01-Bscore-B2B2C
date: 2023-12-20

authors: "Trang Do"
venue: 'Personal Project'
image: "/images/projects/image_bscore1.png"

project_page: "#"
paper: "#"
---

# Applying Behavioral Credit Scoring to B2B2C Models in Vietnam

---

# Applying Behavioral Credit Scoring to B2B2C Models in Vietnam

---

## Overview

Developed a behavioral credit scoring model for a B2B2C lending platform in Vietnam to predict 3-month probability of default (PD) for active customers.

The project implements an end-to-end scorecard development pipeline, including data preparation, feature engineering, model development, validation, and score calibration. The model improves risk segmentation and enables more effective credit decision-making in production environments.

---

## Key Results

* +9 Gini improvement vs baseline model
* Reduced default rate from ~10% → 2.4% (cut-off strategy)
* Improved portfolio profitability: 7.9% → 10%
* Stable model performance (PSI < 0.03 across datasets)

---

## Business Problem

Credit scoring is essential for managing lending risk and maintaining financial stability. Most traditional approaches focus on **application scoring in B2C models**, relying on static customer information at loan origination.

In **B2B2C lending**, customers are accessed indirectly through partner companies, making **behavioral data during the loan lifecycle** a key signal for risk evaluation. However, behavioral scoring in this context remains underexplored, and definitions of default are often inconsistent.

This project addresses these gaps by developing a behavioral scorecard tailored to B2B2C lending, enabling:

* Improved risk segmentation
* Better credit decisions
* More effective credit limit and pricing strategies

---

## Data

The dataset consists of real-world lending data collected from a B2B2C payment platform in Vietnam (2021–2022).

* Dataset size: ~85K records
* Default rate: ~10–12%
* Total features: 456 variables

Feature groups:

* Customer demographics
* Behavioral features
* Employer (partner company) data
* Repayment history

Data quality was evaluated across completeness, accuracy, consistency, timeliness, and uniqueness.

---

## Target Definition

Default is defined based on delinquency behavior:

* **Default (1)**: DPD > 60 within 3 months after scoring
* **Non-default (0)**: DPD ≤ 60

Model scope:

* Active loans only
* DPD ≤ 60 at scoring time
* Minimum 6 months loan history

---

## Methodology

Time-based modeling design:

* Observation window: 12 months before scoring (T0)
* Performance window: 3 months after T0

Data split:

* Train/Test: 70/30
* Out-of-time validation (OOT): Oct 2022 – Jan 2023

---

## Feature Engineering & Selection

From 456 variables, a structured selection process was applied:

* Remove variables with >40% missing values
* Remove highly correlated variables (>70%)
* Apply WOE transformation
* Filter variables using IV (IV ≥ 0.05)
* Apply stepwise selection

This ensures a balance between predictive power, interpretability, and stability.

---

## Model Development

A logistic regression model was used due to its strong performance and interpretability in credit risk modeling.

The model estimates probability of default (PD) based on transformed behavioral features.
The framework can be extended to gradient boosting or deep learning models for further comparison.

---

## Model Selection

Two model variants were evaluated:

* Model 1: partner company identifier only
* Model 2: full partner-related features

Model 2 showed slightly higher Gini, but improvement was marginal.

👉 Model 1 was selected for:

* Simplicity
* Fewer variables
* Better interpretability

---

## Scorecard Scaling & Calibration

Score scaling:

* Range: 0–850
* Base score: 540 ≈ 10% PD
* +40 points → odds double

Calibration ensures predicted PD aligns with observed default rates and remains stable over time.

---

## Model Validation

**Discrimination (Gini):**

* Gini > 80% across train, test, and validation

**Stability (PSI):**

* PSI < 0.03 → strong stability

---

## Deployment

* Automated monthly scoring pipeline using Python and R
* Containerized scoring logic with Docker for reproducibility
* Generated monitoring metrics (Gini, PSI, drift)
* Designed for integration into business decision workflows

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

## Key Learnings

* Behavioral features are more predictive than demographic features in B2B2C
* Simpler models can outperform complex ones in production settings
* Partner-level data provides limited marginal gain
* Time-based validation is critical to avoid optimistic bias

---

## Conclusion

This project demonstrates the effectiveness of behavioral credit scoring in B2B2C lending.

By combining structured feature engineering, interpretable modeling, and production-ready design, the solution delivers strong predictive performance and measurable business impact.

---

## Links

* Project page: *(add deployed link)*

---

