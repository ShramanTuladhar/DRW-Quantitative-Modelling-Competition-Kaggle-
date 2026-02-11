# DRW Crypto Forecasting – Signal Extraction in Noisy Markets

## Overview

This project was developed as part of the DRW Quantitative Modelling Competition (Kaggle).  
The objective was to extract predictive signal from high-frequency cryptocurrency order-book and trade data in an extremely low signal-to-noise environment.

The competition evaluation metric was **Pearson correlation**, requiring models to capture directional information rather than minimise absolute error.

---

## Problem Setting

Financial market data, particularly at high frequency, is dominated by noise.  
The goal of this project was to:

- Predict short-horizon price movement (as defined by the competition target)
- Extract statistically meaningful signal from highly noisy order-book features
- Avoid overfitting in a high-dimensional feature space

This task focused on **correlation-based signal extraction**, similar to an information coefficient (IC) framework used in quantitative trading.

---

## Data Characteristics

The dataset consisted of:

- Order-book features (bid/ask quantities and related measures)
- Trade activity metrics
- 800+ engineered and provided features

Key challenges included:

- Extremely low signal-to-noise ratio
- High dimensionality
- Non-stationarity
- Risk of overfitting due to feature richness

---

## Feature Engineering

Feature construction focused on microstructure-inspired signals:

- Order book imbalance measures  
- Rolling liquidity and volume statistics  
- Short-horizon volatility tagging  
- Lagged features for temporal structure  

Dimensionality reduction using **Principal Component Analysis (PCA)** was applied to mitigate noise and redundancy in the feature set.

The emphasis was on extracting robust structural signal rather than increasing model complexity.

---

## Modelling Approach

Multiple modelling approaches were tested:

- Linear models
- Gradient boosting models (XGBoost, LightGBM, CatBoost)
- Neural network architectures

Time-aware validation was used to prevent leakage and preserve temporal structure.

Model complexity was deliberately controlled to prioritise generalisation over overfitting.

---

## Evaluation

Primary metric: **Pearson correlation**

Final out-of-sample correlation achieved: **~0.07**

In the context of high-frequency financial data, correlation values of this magnitude can represent statistically meaningful signal when extracted from highly noisy environments.

Evaluation focused on:

- Stability across validation folds
- Avoiding feature leakage
- Robustness rather than leaderboard over-optimisation

---

## Key Takeaways

- High-frequency financial data contains extremely weak but exploitable signal.
- Feature engineering often matters more than model complexity.
- Dimensionality reduction can improve stability in noisy environments.
- Correlation-based objectives align more closely with trading signal extraction than RMSE-style metrics.

---

## Future Improvements

If revisiting this project, I would:

- Implement stricter walk-forward validation
- Evaluate feature importance stability across time
- Test explicit regime segmentation
- Convert predictions into simulated trading signals to evaluate risk-adjusted performance

---

## Tools Used

- Python  
- NumPy  
- Pandas  
- scikit-learn  
- XGBoost / LightGBM / CatBoost  
- PyTorch  

---

## Disclaimer

This project was conducted within the constraints of the competition environment and uses only the provided dataset. No proprietary strategies or confidential information are included.
