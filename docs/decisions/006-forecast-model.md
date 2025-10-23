---
status: "accepted"
date: 2025-10-22
decision-makers: [Nimrod Architecture Team]
consulted: [Data Science Team]
informed: [Engineering and Product Teams]
---

# Demand Forecasting with LightGBM Machine Learning Model

## Context and Problem Statement

MobilityCorp needs to optimize fleet redistribution across service areas to meet customer demand. Demand varies significantly based on seasonal patterns, weather conditions, time of day, day of week, and local events. We need accurate demand forecasts at the zone level to proactively move vehicles from low to high demand areas, reducing customer wait times and maximizing vehicle utilization. How should we approach demand forecasting to enable effective fleet redistribution decisions?

Key forecasting requirements:
- Predict demand by different zones in the city
- Account for seasonality
- Use external data including weather, commute patterns, events, and holidays
- Update forecasts frequently

## Considered Options

* Option 1: ML Forecast with Facebook Prophet
* Option 2: ML Forecast with LightGBM
* Option 3: Generative AI Forecast using LLMs
* Option 4: Statistical Forecast

## Decision Outcome

Chosen option: "Option 2: Machine Learning with LightGBM", because it provides the best balance of accuracy for multi-variable forecasting, handles non-linear relationships between weather and time based features, trains quickly, and offers strong feature insights. LightGBM is great at capturing complex interactions between weather, time, and location that drive demand patterns.

Backup option is to do ML forecasting with Facebook Prophet due to the simplicity of the solution, yet with lower quality results. Could be a good minimal viable product release.

## Pros and Cons of Options

### Option 1: Machine Learning with Facebook Prophet

* Good, because it's designed specifically for time series data with strong support for seasonality
* Good, because it provides trends and interpretations making it easy to explain forecasts
* Good, because it handles missing data gracefully and provides uncertainty intervals for forecast confidence without additional configuration
* Good, because it requires minimal tuning and works well with defaults, reducing time to deploy
* Good, because it's fast to train and generate forecasts, enabling frequent updates for operational decisions
* Bad, because it has limited ability to incorporate weather features as external regressors compared to multivariate ML methods
* Bad, because it assumes additive or multiplicative seasonality and may miss complex non-linear interactions between weather, time, and demand
* Bad, because it requires building separate models per zone rather than learning patterns across locations
* Bad, because it may underperform when demand is heavily driven by external factors like temperature or precipitation
* Bad, because it cannot easily capture spatial relationships

### Option 2: Machine Learning with LightGBM (Gradient Boosting)

* Good, because it provides superior accuracy for multiple variable forecasting and automatically learns complex non-linear interactions between weather, time, and demand
* Good, because it handles mixed data types seamlessly and provides feature importance analysis revealing key demand drivers for business insights
* Good, because it has fast training speed enabling frequent model retraining with new data to adapt to changing patterns
* Good, because it can incorporate spatial features like neighboring station demand and model multiple zones simultaneously with location features
* Good, because it's robust to outliers and missing values in weather data while supporting GPU acceleration

* Bad, because it requires extensive feature engineering to create time-based, lagged, and seasonal features from raw data
* Bad, because it needs complex hyperparameter tuning and careful regularization to prevent overfitting with cross-validation
* Bad, because it's less interpretable than Prophet's decomposed components making it harder to explain
* Bad, because it doesn't natively provide uncertainty intervals, requiring additional work with quantile regression or ensembles
* Bad, because it requires ML expertise to properly structure forecasting as a supervised learning problem and build retraining infrastructure

### Option 3: Generative AI Forecast using LLMs

* Good, because it can incorporate unstructured data sources like weather descriptions, event announcements, and news that traditional models cannot process
* Good, because it provides natural language interface allowing non-technical operations staff to query and understand forecasts
* Good, because it can provide narrative explanations alongside numerical predictions for operational recommendations
* Good, because emerging time series foundation models show promise for zero-shot forecasting across different markets
* Good, because it has flexible input format that doesn't require rigid feature engineering pipelines
* Bad, because it's unproven technology for production demand forecasting with accuracy typically lower than specialized ML methods
* Bad, because it has significantly higher inference costs and latency concerns that may prevent generating forecasts quickly enough for operations
* Bad, because the black box nature makes debugging forecast errors extremely challenging and hallucination risk could produce plausible but incorrect forecasts
* Bad, because it's difficult to ensure consistency, reliability, and provide confidence intervals
* Bad, because it requires large compute resources and has immature tooling for production deployment at scale

### Option 4: Statistical Forecasting

* Good, because it has well-established statistical foundation with mathematically rigorous and proven convergence properties
* Good, because it provides confidence intervals based on statistical theory and has interpretable parameters with clear meaning
* Good, because it requires minimal computational resources to train and forecast, working well even with limited historical data
* Good, because it offers transparent and auditable forecasting process suitable for regulatory environments
* Good, because it has no risk of overfitting with proper model selection and easy implementation with standard statistical packages

* Bad, because it assumes linear relationships and cannot capture non-linear weather impacts on demand
* Bad, because it's poor at incorporating external regressors like weather, events, and struggles with multiple seasonal patterns
* Bad, because univariate models miss important multivariate relationships and require stationary data needing extensive preprocessing
* Bad, because it's less accurate than modern ML methods for complex real-world problems with rapid demand changes
* Bad, because it's difficult to scale to hundreds of stations requiring individual models and cannot easily handle categorical features

## Links

* [Facebook Prophet Documentation](https://facebook.github.io/prophet/)
* [LightGBM Documentation](https://lightgbm.readthedocs.io/)
* [Time Series Forecasting Best Practices](https://github.com/microsoft/forecasting)
* [Micromobility Demand Patterns Research](https://journals.sagepub.com/doi/full/10.1177/0361198120917677)