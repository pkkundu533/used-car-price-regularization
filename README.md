## Regularisation in Linear Models — Applied Study

This repository contains an applied analysis of linear regression,
Ridge, and Lasso regularisation on a real-world used-car pricing dataset
(~15,900 records).

The focus is not on algorithm comparison, but on evaluating **when
regularisation meaningfully improves model behaviour** once data is
properly prepared.

---

## Problem Context

Vehicle pricing data contains:
- Strongly skewed target values
- Mixed numerical and categorical features
- Correlated engine-related attributes
- High-cardinality bundled specifications

These characteristics make it a good candidate for testing whether
regularisation improves **generalisation and stability**, not just
accuracy.

---

## Key Engineering Decisions

### Target Handling
- Vehicle prices were heavily right-skewed
- A log transformation was applied to stabilise variance and better
  satisfy linear model assumptions
- The log-transformed price was used as the modeling target

### Feature Engineering
- Rare categorical levels were consolidated to reduce sparsity
- Bundled specification columns were converted into feature-count
  variables to avoid dimensionality explosion
- Original bundled text columns were removed after extraction
- Numerical outliers were capped using IQR-based limits where
  appropriate

### Encoding & Scaling
- Categorical features were one-hot encoded with reference levels
  dropped
- All numerical features were standardised
- Scaling was fit on training data only to prevent leakage

---

## Model Behaviour & Findings

### Baseline Linear Regression
- Achieved ~0.92 R² on both training and test sets
- Low and consistent RMSE and MAE across splits
- No evidence of overfitting
- Residual diagnostics confirmed linearity, symmetry, and
  homoscedasticity

This established a strong and reliable baseline.

### Multicollinearity
- Engine power, displacement, and vehicle weight showed expected
  correlations
- VIF values were moderate and below critical thresholds
- Regularisation was preferred over feature removal

### Ridge Regression
- Improved coefficient stability under multicollinearity
- Test error decreased slightly and then stabilised across a wide
  range of alpha values
- Performance gains were incremental, not dramatic
- Best results occurred in a stable alpha region rather than a sharp
  optimum

### Lasso Regression
- Required very small regularisation strength to match baseline
  performance
- Did not eliminate any features after feature engineering
- Offered no meaningful advantage over Ridge for this dataset

---

## Core Takeaways

- Strong preprocessing mattered more than algorithm choice
- A clean linear baseline already captured most of the signal
- Regularisation primarily improved **stability**, not accuracy
- Ridge was more suitable than Lasso due to correlated predictors
- Feature engineering reduced redundancy before regularisation was
  applied
- Simpler, interpretable models were sufficient for this problem

---

## Why This Matters

In applied ML systems, added complexity must be justified by tangible
benefits.

This analysis reinforces that:
- Regularisation is a tool for robustness and trust
- Baseline validation is essential before introducing more complex
  models
- Well-prepared linear models can perform strongly on structured,
  tabular data

---

## Dataset

AutoScout used car listings (public dataset).  
Original data is not redistributed in this repository.
