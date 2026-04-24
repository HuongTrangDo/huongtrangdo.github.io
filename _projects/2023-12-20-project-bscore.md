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

The project implements a full scorecard development pipeline, including data preparation, feature engineering, model development, validation, and score calibration. The resulting model enables better risk segmentation and supports more effective credit decision-making.

---

## Business Problem

Credit scoring is essential for managing lending risk and maintaining financial stability. Most traditional approaches focus on **application scoring in B2C models**, relying on static customer information at loan origination.

However, in **B2B2C lending**, customers are accessed indirectly through partner companies, and repayment behavior over time becomes a key signal for risk assessment. Despite this, behavioral scoring in this context remains underexplored, and definitions of default are often inconsistent.

This project aims to build a **behavioral scorecard tailored to B2B2C lending**, enabling:

* Improved risk-based segmentation
* Better credit decision-making
* More efficient credit limit and pricing strategies

---

## Data

The dataset consists of real-world lending data collected from a B2B2C payment platform in Vietnam (2021–2022).

Loans are issued to employees of partner companies, with repayments partially deducted from salaries. This provides richer information compared to traditional B2C datasets.

* Dataset size: ~85K records
* Default rate: ~10–12%
* Features: 456 variables

Feature groups:

* Customer demographics
* Behavioral features
* Employer (partner company) data
* Repayment history

Data quality was assessed across:

* Completeness
* Accuracy
* Consistency
* Timeliness
* Uniqueness

---

## Target Definition

Default is defined using delinquency behavior based on Roll Rate and Vintage analysis:

* **Default (1)**: DPD > 60 within 3 months after scoring
* **Non-default (0)**: DPD ≤ 60

The model predicts 3-month PD for customers who:

* Have active loans
* Have DPD ≤ 60 at scoring time
* Have at least 6 months of loan history

---

## Methodology

A time-based modeling framework was applied:

* **Observation window**: 12 months before scoring (T0)
* **Performance window**: 3 months after T0

Data split:

* Train/Test: 70/30
* Out-of-time validation (OOT): Oct 2022 – Jan 2023

This setup ensures realistic evaluation and prevents data leakage.

---

## Feature Engineering & Selection

From 456 variables, a structured selection process was applied:

### Data Filtering

* Remove variables with >40% missing values
* Remove highly correlated variables (>70%)

### Transformation

* Apply **WOE (Weight of Evidence)**
* Evaluate using **Information Value (IV)**
* Remove variables with IV < 0.05

### Selection

* Apply **stepwise regression** to select optimal features

---

## Model Development

A **logistic regression model** was used due to:

* Strong performance in credit risk modeling
* High interpretability
* Regulatory compatibility

The model estimates probability of default based on transformed behavioral features.

---

## Model Selection

Two model variants were evaluated:

* **Model 1**: Uses only partner company identifier
* **Model 2**: Uses full partner-related features

Although Model 2 achieved slightly higher Gini, the improvement was marginal.

👉 Model 1 was selected due to:

* Simplicity
* Fewer variables
* Better interpretability

---

## Scorecard Scaling & Calibration

### Score Scaling

Model outputs (log-odds) were transformed into a credit score range of **0–850**, aligned with FICO-style scoring.

* Base score: 540 corresponds to ~10% PD
* Each +40 points → odds double

Customers are segmented into risk bands based on score ranges.

---

### Calibration

Calibration adjusts predicted PD to match observed default rates over time.

This ensures:

* Model stability
* Alignment with real-world behavior
* Robustness to population and economic changes

---

## Model Validation

### Discrimination (Gini)

The model demonstrates strong discriminatory power:

* Gini > 80% across train, test, and validation sets

ROC curves show strong separation between default and non-default customers.

---

### Stability (PSI)

Population Stability Index (PSI):

* Test vs Train: ~0.02
* OOT vs Train: ~2.47

👉 Indicates high model stability over time.

---

## Business Impact

Applying the scorecard enables:

### 1. Risk-based Segmentation

Customers are grouped into risk bands (C → AAA)

* Rejecting lowest segment reduces default rate:

  * From ~10% → ~2.4%

---

### 2. Credit Policy Optimization

* Increase credit limits for low-risk segments
* Reduce exposure for high-risk segments

---

### 3. Risk-based Pricing

Comparison of strategies:

* **Baseline**: Flat interest rate (55%)
* **With scoring**:

  * Risk-based pricing
  * Cut-off for high-risk segment

👉 Result:

* Profit improves from **7.9% → 10%**
* While reducing overall portfolio risk

---

## Key Takeaways

* Behavioral data significantly improves risk prediction in B2B2C lending
* Logistic regression remains highly effective for scorecard modeling
* Simpler models can deliver strong performance with better interpretability
* Time-based validation and calibration are critical for production readiness

---

## Conclusion

This project demonstrates the effectiveness of behavioral credit scoring in B2B2C lending environments.

By combining structured feature engineering, logistic regression, and scorecard calibration, the model achieves strong predictive performance and enables practical business applications in risk management and decision-making.

---

## Links
* Project page: *(add deployed link)*
---

