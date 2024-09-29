# Measuring Risk in Fixed Income Portfolios using Yield Curve Models

**Group Members**: Wenqiang Zhang, Baocheng Jiao, Chi-Lin Li, Wenlin Tang, Zhixin Zhang, Yinbo Zhao, Yemei Liang  
**Date**: May 3, 2024

## Project Overview

This project presents a risk management framework for fixed income portfolios using yield curve models. The focus is on **Value at Risk (VaR)** and **Expected Shortfall (ES)**, which are critical measures of market risk for bond portfolios. The project implements **dynamic factor models** (Nelson-Siegel and Svensson) along with **GARCH-type models** to estimate the conditional covariance matrix of bond returns, and uses these estimates to calculate out-of-sample VaR for bond portfolios.

### Key Features:
- **Dynamic Yield Curve Models**: Application of the Nelson-Siegel and Svensson models to estimate the yield curve.
- **Risk Metrics**: Calculation of Value at Risk (VaR) and Expected Shortfall (ES) using out-of-sample data.
- **GARCH-type Models**: Dynamic Conditional Correlation (DCC-GARCH) model is employed to estimate the conditional volatility and correlation of bond returns.
- **Empirical Validation**: Application to U.S. Treasury yields from January 2019 to December 2023, covering a wide range of maturities (1 month to 30 years).

## Methodologies

### 1. Yield Curve Estimation
- **Nelson-Siegel Model**: Captures the yield curve’s level, slope, and curvature.  
  $$
  y(t) = \beta_0 + \beta_1 \frac{1 - e^{-t/\tau}}{t/\tau} + \beta_2 \left( \frac{1 - e^{-t/\tau}}{t/\tau} - e^{-t/\tau} \right)
  $4
- **Svensson Model**: Extends Nelson-Siegel by adding additional factors for a better fit, particularly for long maturities.

### 2. Conditional Covariance Matrix
- **DCC-GARCH Model**: Dynamic Conditional Correlation (DCC) combined with GARCH is used to estimate the covariance matrix of bond returns.  
  \[
  Q_t = (1 - \alpha - \beta) Q + \alpha z_{t-1} z_{t-1}^T + \beta Q_{t-1}
  \]
  This approach allows for time-varying correlations between the factors driving the yield curve.

### 3. Risk Measurement
- **Value at Risk (VaR)**: Measures the potential maximum loss over a given time horizon at a specific confidence level.
- **Expected Shortfall (ES)**: Represents the average loss beyond the VaR threshold, providing a more comprehensive view of tail risk.

### 4. Empirical Backtesting
- The models are backtested using historical U.S. Treasury yield data to evaluate the accuracy of the VaR estimates.
- **Exceedance Rates**: The backtest results show that the Svensson model combined with DCC-GARCH performs better in predicting extreme risk events compared to the Nelson-Siegel model.

## Empirical Results

The empirical study uses five years of daily yield curve data from U.S. Treasury securities (2019–2023). The key findings from backtesting include:

- **Nelson-Siegel Model with AR/DCC-GARCH**: VaR exceedance rate of 7.14%.
- **Nelson-Siegel Model with VAR/DCC-GARCH**: VaR exceedance rate of 7.46%.
- **Svensson Model with AR/DCC-GARCH**: VaR exceedance rate of 2.49%, significantly improving predictive accuracy.
- **Svensson Model with VAR/DCC-GARCH**: VaR exceedance rate of 2.49%, maintaining a high level of accuracy across different model configurations.

### Performance Summary:
- **VaR at 1% confidence level**: Svensson model configurations yielded the most accurate risk predictions.
- **Expected Shortfall**: The Svensson/DCC-GARCH model showed superior performance in managing extreme tail risks.

## Conclusion

This project demonstrates the effectiveness of dynamic yield curve models and GARCH-type models in measuring and predicting risk in fixed income portfolios. The results indicate that the **Svensson model** combined with **DCC-GARCH** provides more accurate risk assessments for bond portfolios, particularly in predicting extreme losses. Future work could explore the application of these models in different market environments and for other types of fixed income securities.

## Installation

To replicate this project, you need to install the following dependencies:

```bash
pip install numpy pandas statsmodels arch matplotlib
```

## Usage

1. **Preprocess Data**: Import and clean U.S. Treasury yield data, ensuring it spans multiple maturities and dates.
2. **Run Yield Curve Models**: Implement the Nelson-Siegel and Svensson models to estimate the term structure of interest rates.
3. **Risk Calculation**: Use the GARCH-type models to calculate VaR and ES based on the conditional covariance matrix.
4. **Backtesting**: Backtest the models with historical data to validate the performance of the VaR estimates.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contribution

Group members Wenqiang Zhang, Baocheng Jiao, Chi-Lin Li, Wenlin Tang, Zhixin Zhang, Yinbo Zhao, and Yemei Liang contributed equally to this project.
