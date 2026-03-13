# New York Gasoline Price Time Series Analysis (1986–2026)
## Project Overview
This project analyzes weekly New York Harbor gasoline prices from 1986 to 2026 using time series modeling techniques. The goal is to understand the statistical properties of gasoline prices, evaluate forecasting performance, and model the volatility dynamics of price changes.

The analysis applies a combination of ARIMA modeling for the mean process and GARCH modeling for time-varying volatility, a framework commonly used in financial and commodity price analysis.

## Dataset
The dataset contains weekly gasoline prices in New York Harbor covering approximately 40 years of observations.

Key characteristics:
- Frequency: Weekly
- Time span: 1986–2026
- Variable: Gasoline price ($ per gallon)

## Methodology
1. Data Transformation
A log transformation was applied to stabilize variance and allow price changes to be interpreted as percentage returns.

2. Exploratory Analysis
- Time series visualization
- STL decomposition to examine trend and seasonality

Findings:
- Strong long-term upward trend
- Weak seasonal patterns
- Large fluctuations associated with major economic shocks

3. Stationarity Testing
Stationarity was evaluated using:
- ACF and PACF plots
- Augmented Dickey–Fuller (ADF) test

Results:
- Log price series was non-stationary
- First differencing produced a stationary return series

4. ARIMA Model Selection
Based on ACF/PACF patterns, several candidate models were estimated:
- ARIMA(2,1,1)
- ARIMA(3,1,1)
- ARIMA(4,1,1)
- ARIMA(2,1,2)
Models were compared using:
- AIC
- BIC
- Log-likelihood
- Residual variance
The model that produced the lowest information criteria values and best overall fit was ARIMA(4,1,1).

5. Model Validation
Model performance was evaluated using:
- Residual diagnostics
- Ljung–Box test
- Train/test forecasting
- Rolling forecast cross-validation
Findings:
- Residuals behave approximately as white noise
- Forecast accuracy was similar to a naive random walk forecast

This indicates gasoline prices behave similarly to a random walk process, making directional forecasting difficult.

6. Forecasting
The final ARIMA model was refit using the full dataset and used to generate a 52-week (1-year) forecast.

Key insight:
- Point forecasts remain near the most recent observed price level
- Prediction intervals widen over time due to increasing uncertainty

This behavior is typical for commodity price series.

7. Volatility Analysis
The return series showed clear volatility clustering, confirmed by the ARCH LM test.
To capture this behavior, a GARCH(1,1) model was estimated.

Key findings:
- Significant ARCH and GARCH parameters
- High volatility persistence (α + β ≈ 0.92)
- Volatility shocks decay gradually over time

The estimated volatility half-life is approximately 8 weeks, meaning shocks take several weeks to dissipate.

8. Structural Breaks
The analysis also highlights major structural disruptions in gasoline prices, including:
- 2008 Financial Crisis
- 2020 COVID-19 Demand Collapse
- 2022 Global Energy Shock

These events correspond to significant spikes in both price movements and volatility.

## Key Insights

• Gasoline prices exhibit random walk behavior, making directional forecasting difficult.
• Volatility is time-varying and persistent, with clear clustering patterns.
• Major economic events produce large structural breaks in price dynamics.
• ARIMA models capture the mean process, while GARCH models effectively model volatility.

## Tools & Libraries 
R packages used in this analysis:
- forecast
- tseries
- rugarch
- ggplot2
- dplyr
- readxl
- xts





  
