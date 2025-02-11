Task 1 - DashBoard
1. Title
Global Population Estimates and Projection: Provides a high-level overview of population statistics and trends worldwide.
2. Interactive Map
Country Name Visualization:
Displays the global distribution of population data with markers indicating specific countries.
Helps users quickly identify geographic regions of interest.
3. Decomposition tree
Region, Rural, and Urban Population Breakdown:
Visualizes the flow of population data from Region → Rural Population → Urban Population.
Includes income group details (e.g., "Low Income").
Useful for understanding demographic distribution and urbanization trends across different regions.
4. Bar Chart
Male and Female Population by Country:
Highlights gender distribution for key countries like China, India, and the United States.
Provides a quick comparison of male vs. female populations in the most populous countries.
5. Pie Chart
Average Life Expectancy by Region:
Shows the percentage contribution of different regions to global average life expectancy.
Regions like Europe & Central Asia and North America demonstrate higher life expectancies compared to others.
6. Line Chart
Urban vs. Rural Population Over Time:
Depicts the growth trends of Rural and Urban populations over time.
Offers insights into urbanization trends and rural depopulation.
7. KPI Cards
Key Performance Indicators (KPIs):
Birth Rate: 26.67
Death Rate: 10.16
Sum of Rural Population: 276 billion
Sum of Urban Population: 312 billion
These figures give an at-a-glance understanding of demographic metrics.
8. Filters
Region and Income Group:
Allows users to drill down into specific subsets of data.
Options include:
East Asia & Pacific
Europe & Central Asia
Latin America & Caribbean


Task 2 - STATISTICAL ANALYSIS
1. Libraries and Data Loading
Libraries Used:
EDA and Visualization: readxl, ggplot2, dplyr, GGally, corrplot
Modeling: mgcv, randomForest, e1071, caret
Hypothesis Testing: reshape2, car
Dataset: Energy Efficiency Data.xlsx
The columns are renamed for consistency by replacing spaces with underscores.
2. Exploratory Data Analysis (EDA)
Objectives:
Understand the dataset structure.
Identify data distributions, relationships, and outliers.
Key Steps:
Summary Statistics:
Outputs mean, median, min, and max for each variable.
Missing Value Check:
Ensures completeness of the dataset.
Distribution Analysis:
Plots histograms for each feature to visualize spread and skewness.
Outlier Detection:
Boxplots for all numerical variables to identify extreme values.
Outliers are quantified using the Interquartile Range (IQR) method.
Correlation Analysis:
A correlation matrix is computed and visualized to understand relationships between variables.
Key Insight: Strong correlation between Heating and Cooling Load.
3. Correlation Analysis
Objective:
Quantify and interpret the linear relationship between Heating Load and Cooling Load.
Steps:
Pearson Correlation:
Measures the strength of the linear relationship.
Result: A strong positive correlation.
Scatter Plot:
Visualizes the relationship with a linear regression trendline.
Interpretation:
Heating and Cooling Loads are highly dependent, likely driven by common factors.
4. Regression Models
Goal:
Predict Heating and Cooling Loads using structural and environmental features.
Models:
Random Forest Regression:
Features: All numerical and categorical predictors.
Performance:
Heating Load RMSE: <value calculated in script>.
Cooling Load RMSE: <value calculated in script>.
Random Forest outperformed other models in accuracy.
Support Vector Regression (SVR):
Models non-linear relationships with radial kernel.
Performance:
Heating Load RMSE: <value calculated in script>.
Cooling Load RMSE: <value calculated in script>.
Generalized Additive Model (GAM):
Provides flexible modeling of smooth relationships.
Performance:
Heating Load RMSE: <value calculated in script>.
Cooling Load RMSE: <value calculated in script>.
Diagnostics:
Diagnostic plots for each model (Residual plots, Predicted vs Actual plots) provide insights into model performance.
5. Hypothesis Testing
Purpose:
Assess statistical differences and relationships in the dataset.
Tests:
Shapiro-Wilk Test:
Checks for normality of Heating and Cooling Load distributions.
Kruskal-Wallis Test:
Compares Heating and Cooling Load medians across different orientations.
Mann-Whitney U Test:
Evaluates differences in loads between high and low glazing areas.
Spearman's Rank Correlation:
Measures monotonic relationships between Heating and Cooling Loads.
Friedman Test:
Tests differences in Heating Load across simulated orientations.
Results:
Statistically significant relationships observed between features and energy loads.
6. Summary of Findings
EDA Insights:
Heating and Cooling Loads are highly correlated.
Significant outliers identified in numerical variables.
Modeling Results:
Random Forest is the best-performing model.
GAM and SVR provide competitive alternatives.
Hypothesis Testing:
Orientation and Glazing Area influence energy loads significantly.
Non-normal distributions in energy loads necessitate non-parametric tests.


Task 3 - TIME SERIES ANALYSIS
1. Loading and Preprocessing
Dataset: AAPL.csv
The script loads and preprocesses the dataset, ensuring:
Proper date formatting.
Sorting data chronologically.
Focus Feature: "Close" prices of AAPL stock are extracted and converted into a time series object for analysis.
2. Visualizing the Time Series
Plot: Raw time series of closing prices.
Purpose: Identify overall trends and possible seasonality in the data.
3. Decomposing the Time Series
The series is decomposed into:
Trend: Long-term movement.
Seasonality: Recurring patterns.
Residuals: Irregular fluctuations.
Visualization: The decomposition plot helps to interpret these components.
4. Stationarity Check
Augmented Dickey-Fuller (ADF) Test:
Determines if the time series is stationary.
If non-stationary, the series is differenced.
Output:
ADF test statistic and p-value.
If p-value > 0.05, the series is differenced to achieve stationarity.
5. Splitting the Data
The dataset is divided into:
Training Set (80%): For model building.
Testing Set (20%): For evaluation.
Training Data: Converted into a time series object for models requiring seasonality.
6. Forecasting Models
Three forecasting models are applied:

Model 1: ARIMA (AutoRegressive Integrated Moving Average)
Process:
Automatically selects the best ARIMA parameters.
Fits the model to the training set.
Forecast:
Predicts the testing set.
Produces a visualization of forecasted vs actual values.
Metrics:
Root Mean Square Error (RMSE).
Mean Absolute Error (MAE).
Model 2: Holt-Winters (HW)
Seasonality: Multiplicative.
Process:
Fits the model to the training data.
Handles both trend and seasonal components.
Forecast:
Visual comparison with the actual values.
Metrics:
RMSE and MAE computed for evaluation.
Condition:
Requires sufficient data length for seasonal patterns.
Model 3: Simple Exponential Smoothing (SES)
Applicability:
Ideal for series with no clear trend or seasonality.
Process:
Forecasts the testing set.
Metrics:
RMSE and MAE calculated.
7. Comparing Models
RMSE and MAE for each model are summarized in a table.
Best Model:
The model with the lowest RMSE is selected as the best-performing model.
8. Exponential Moving Average (EMA)
Purpose: Smoothens the time series to highlight trends.
Process:
A 50-day EMA is computed.
Visualization:
Closing prices are plotted alongside the EMA.
