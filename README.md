# Time Series Forecasting using Linear Models

This repository contains a Kaggle notebook demonstrating various time series forecasting techniques using linear models. The project focuses on comparing different models' performance on a pre-selected dataset.

## Table of Contents
1. [Introduction](#introduction)
2. [Dataset](#dataset)
3. [Methodology](#methodology)
4. [Models Implemented](#models-implemented)
5. [Benchmarking](#benchmarking)
6. [Results](#results)
7. [Installation and Usage](#installation-and-usage)
8. [Contributing](#contributing)
9. [License](#license)

## Introduction

Time series forecasting is a critical task in many industries, from finance to energy management. This project aims to compare the performance of various linear models in forecasting time series data. We implement and evaluate several popular techniques, providing insights into their strengths and weaknesses.

## Dataset

The analysis uses the "DailyDelhiClimateTest.csv" dataset, which contains daily climate data for Delhi. Here are the key details about the dataset:

- **Source**: "/kaggle/input/DailyDelhiClimateTrain.csv"
- **Time Range**: The data spans from January 1, 2013 to January 1, 2017 
- **Features**:
  1. date: The date of the observation (YYYY-MM-DD format)
  2. meantemp: Mean temperature for the day (in Celsius)
  3. humidity: Humidity level (percentage)
  4. wind_speed: Wind speed (in km/h)
  5. meanpressure: Mean atmospheric pressure (in hPa)

The dataset provides a comprehensive view of Delhi's daily climate conditions, including temperature, humidity, wind speed, and atmospheric pressure. This rich set of features allows for in-depth analysis and forecasting of weather patterns in Delhi.

## Methodology

Our approach involves the following steps:
1. Exploratory Data Analysis (EDA)
2. Feature Engineering
3. Model Implementation
4. Model Evaluation and Comparison

## Models Implemented

We implemented and compared the following models:
1. ARIMA (Autoregressive Integrated Moving Average)
2. ARIMAX (ARIMA with Exogenous Variables)
3. SARIMAX (Seasonal ARIMAX)
4. Linear Regression
5. Ridge Regression
6. Lasso Regression

## Benchmarking

To ensure a fair comparison, we utilized the Libra benchmarking tool. This allowed us to evaluate each model's performance across various metrics consistently.
To benchmark the models you have trained for time series forecasting, you need to calculate the following performance measures:

### 1. Forecast Error Measures
These measures assess the accuracy of your forecasts by comparing them to the actual observed values. The benchmark includes six specific error measures:

> Symmetrical Mean Absolute Percentage Error (sMAPE)

$$e_{sM} = \frac{200\%}{k} \sum_{t=1}^{k} \frac{|y_t - \hat{y}_t|}{|y_t + \hat{y}_t|}$$

> Mean Absolute Scaled Error (MASE)

$$e_{MA} = 
\frac{1}{k} \sum_{t=1}^{k} \frac{|y_t - \hat{y}_t|}{\frac{1}{n-m} \sum_{i=m+1}^{n} |y_i - y_{i-m}|}$$

> Mean Wrong-Estimation Shares ($\rho_U$ and $\rho_O$)

$$
\rho_U = \frac{1}{k} \sum_{t=1}^{k} \max(\text{sgn}(y_t - \hat{y}_t), 0)
$$


$$
\rho_O = \frac{1}{k} \sum_{t=1}^{k} \max(\text{sgn}(\hat{y}_t - y_t), 0)
$$

> Mean Wrong-Accuracy Shares ($\delta_U$ and $\delta_O$)

$$
\delta_U = \begin{cases} 
\frac{1}{k \cdot \rho_U} \sum_{t=1}^{k} \frac{\max(y_t - \hat{y}_t, 0)}{|y_t|}, & \text{if } \rho_U > 0 \\
0, & \text{otherwise}
\end{cases}
$$

$$
\delta_O = \begin{cases} 
\frac{1}{k \cdot \rho_O} \sum_{t=1}^{k} \frac{\max(\hat{y}_t - y_t, 0)}{|y_t|}, & \text{if } \rho_O > 0 \\
0, & \text{otherwise}
\end{cases}
$$

> The Mean Squared Error (MSE)

$$
\text{MSE} = \frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2
$$

> Coefficient of Determination (R²)

 $$\text{R^2} = 1 - \frac{\sum_{i=1}^{n} (y_i - \hat{y}_i)^2}{\sum_{i=1}^{n} (y_i - \bar{y})^2}$$

These measures provide insights into the average magnitude of under- and over-estimations.

### 2. Time-to-Result
This measure evaluates the efficiency of the forecasting method by timing how long it takes to produce a forecast. The process involves:

- **Normalization**: The time-to-result for each method is normalized by comparing it to the time taken by a seasonal naive (sNaive) method. This ensures comparability across different hardware and operating systems.

### Benchmarking Process
1. **Data Splitting**: The time series is divided into training (80%) and test (20%) sets.
2. **Multi-Step-Ahead Forecast**: Perform forecasts iteratively over different parts of the time series, typically forecasting the next 20% of the time series at each step.
3. **Average Measures**: Calculate the average and standard deviation of each performance measure.
4. **Reporting**: Prepare a benchmarking report detailing the performance of the forecasting methods.

These measures collectively provide a comprehensive evaluation of both the accuracy and efficiency of  time series forecasting models

## Results

The notebook includes detailed comparative analysis of the models, including:
- Performance across various benchmarks
- Graphical comparisons of predictions vs. actual values
- Discussion of each model's strengths and weaknesses

These can be found in Notebook.

## Installation and Usage

To run this notebook:
1. Clone this repository
2. Install the required dependencies (listed in the notebook)
3. Open the notebook in Jupyter or your preferred environment
4. Run the cells sequentially

## Contributing

Contributions to improve the analysis or extend it to other models are welcome. Please feel free to fork the repository and submit a pull request.

## License
This project is licensed under the MIT License - see the LICENSE file for details.


For any questions or feedback, please open an issue in this repository.
