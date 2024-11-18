# ARIMA and SARIMAX Time Series Forecasting

This repository contains the Jupyter Notebook `ARIMA_and_SARIMAX.ipynb`, which demonstrates the application of ARIMA (AutoRegressive Integrated Moving Average) and SARIMAX (Seasonal AutoRegressive Integrated Moving Average with eXogenous variables) models for time series analysis and forecasting. The notebook is designed to provide insights into effective strategies for modeling and predicting data that exhibits seasonal patterns.

## Project Description

The `ARIMA_and_SARIMAX.ipynb` notebook explores time series forecasting by:
- Introducing the concepts of ARIMA and SARIMAX models.
- Demonstrating the data preparation steps necessary for time series analysis.
- Implementing these models on sample datasets to forecast future data points.
- Analyzing the sales 
- The primary objective is to forecast future sales accurately.

---

## Data Overview

The dataset includes:
- **Month**: The observation month.
- **Sales**: Monthly champagne sales (in millions).

The data spans from January 1964 to September 1972.

---

## Data Preprocessing

### Steps Taken:
1. Renamed columns for clarity.
2. Converted the `Month` column to a datetime format.
3. Set `Month` as the index.
4. Removed missing values.

**Graph 1**: Initial data visualization showing raw sales trends.
<img width="623" alt="image" src="https://github.com/user-attachments/assets/efd676ad-bd80-4236-a96f-037a8e751a91">

---

## Exploratory Data Analysis (EDA)

### Descriptive Statistics

**Graph 2**: Summary of descriptive statistics for the `Sales` column, showing mean, standard deviation, and percentiles.
<img width="160" alt="image" src="https://github.com/user-attachments/assets/92a13cec-6cea-4284-a519-856bd38e823b">

---

## Testing for Stationarity

- Used the **Augmented Dickey-Fuller (ADF) Test**.
- **Null Hypothesis (H0)**: The data is non-stationary.
- The test results showed:
  - ADF Test Statistic: -1.83
  - p-value: 0.36  
**Conclusion**: Weak evidence to reject H0, indicating the data is non-stationary.

**Graph 3**: ADF test result output.
<img width="929" alt="image" src="https://github.com/user-attachments/assets/4431b685-7107-4629-8eea-b96399547ae7">

---

## Data Transformation: Differencing

Performed the following transformations to stationarize the data:
1. **First Differencing**: Accounts for changes between consecutive months.  
   **Graph 4**: Plot of first-differenced data.
   <img width="297" alt="image" src="https://github.com/user-attachments/assets/f9c62d21-a584-4bd4-bc93-2026442de93b">

3. **Seasonal Differencing**: Captures changes across months of the same season.  
   **Graph 5**: Plot of seasonally differenced data.
   <img width="632" alt="image" src="https://github.com/user-attachments/assets/1e6ec0f6-4a8e-469a-9c1c-fab290a03af3">


After seasonal differencing:
<img width="1005" alt="image" src="https://github.com/user-attachments/assets/37f49b3c-0b25-4834-9bbd-7172db4e1114">

- ADF Test Statistic: -7.63
- p-value: ~0.00  
**Conclusion**: Data is stationary.

---

## Autocorrelation and Partial Autocorrelation

Analyzed autocorrelation (ACF) and partial autocorrelation (PACF) to determine ARIMA parameters:
- **AR Model Identification**: Used PACF.
- **MA Model Identification**: Used ACF.

**Graph 6**: ACF plot.  

**Graph 7**: PACF plot.

---

## Model Building and Evaluation

### ARIMA Model
- Parameters: (p, d, q) = (1, 1, 1).
- Summary:
  - AIC: 1911.63
  - Log Likelihood: -952.81
- Limitations: Unable to model seasonality effectively.

### SARIMAX Model
- Parameters: (p, d, q, s) = (1, 1, 1, 12).
- Added seasonal components to improve predictions.
- Performed better than ARIMA for this dataset.

---

## Forecasting

### ARIMA Forecast
- Forecasted sales for 14 months.
- **Graph 10**: ARIMA forecast plot, showing predicted vs actual values.
<img width="901" alt="image" src="https://github.com/user-attachments/assets/73922fd0-9228-4af3-a2d0-cc06acee880f">

### SARIMAX Forecast
- Extended forecast to 24 months with seasonal adjustments.
- **Graph 11**: SARIMAX forecast plot.
<img width="896" alt="image" src="https://github.com/user-attachments/assets/e53b7d21-3e3b-41b9-baa5-83231e34ba81">

---

## Insights

1. **Seasonality**: Sales exhibit clear seasonal trends.
2. **Stationarity**: Seasonal differencing was crucial for stationarizing the data.
3. **Model Comparison**: SARIMAX outperformed ARIMA due to its ability to model seasonality.
4. **Forecast Accuracy**: Results can assist in planning inventory and optimizing sales strategies.

---

## Future Directions

1. Incorporate external variables like holidays and promotions to improve model accuracy.
2. Use grid search for automated parameter tuning.
3. Explore ensemble models for better performance.

---

## Appendix

### Full Code and Outputs
The full code, including data preprocessing, visualization, and model building, is available in the `scripts` directory.

### Dependencies
- Python Libraries: `numpy`, `pandas`, `matplotlib`, `statsmodels`.


## Acknowledgments

- Dataset is downloaded from Kaggle: https://www.kaggle.com/datasets/anupamshah/perrin-freres-monthly-champagne-sales?resource=download
- Inspiration or articles that helped shape this project: (https://www.youtube.com/@krishnaik06)
