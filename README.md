# Oil-Price-Prediction-LSTM-XGBoost
# Model - 1
The model is built using Long Short Term Memory (LSTM) and fbProphet to predict Daily Close Price using previous data of Close Price.

## Approach -
- “Crude_All.csv” data imported.
- Exploratory Data Analysis - 
  - Dropped useless columns.
  - Added columns derived from “Date” column using add_datepart() from fastai.tabular.
  - Converted the “Date” column to the index of DataFrame.
  - Drop Null/NA/NaN values.
  - Drop values less than or equal to 0 (zero).
  - Plot a Graph for Close Prices per Year.
  - Plot a Graph for Aggregate Monthly Trends over the Years.
- Other Outlier Detection -
  - Create a new column “SimpleReturn” which contains the value of (Present Day Close Price - Previous Day Close Price) / (Previous Day Close Price)
  - Calculate the Mean and Standard Deviation of the column “SimpleReturn”
  - Plot a Histogram for “SimpleReturn”
  - Perform the “Kolmogorov-Smirnov Test” (“kstest”) to check if the data follows a particular distribution. Specifically Normal Distribution.
  - As the Null Hypothesis is accepted with pvalue=0.0, the distribution is Normal.
  - Remove data points out of 3*(Standard Deviation) range following The Empirical Rule that 99.7% of data observed following a Normal Distribution lies within 3 Standard Deviations of the Mean.
- Prediction using LSTM -
  - LSTM uses the concept of Long Short Term Memory. This concept works by predicting the next value using the given “Short” input while also keeping in mind the key values from “Long” memory.
  - LSTM is trained using previous 90 Days data to predict the next 1 Day Close Price.
  - Model Training, Testing, and Validation are plotted.
- Prediction using fbProphet - 
  - Prophet uses specific DataFrame column names as “ds” for “Date” and “y” for Dependent Variable.
  - Converted the DataFrame in the required format.
  - Trained Prophet model on the whole DataSet and Predicted the values for next year.
  - The predictions show a lot of variances.

# Model - 2
The model is built using Polynomial Regression and fbProphet to predict Quarterly Returns using previous Quarterly Return Price data.

## Approach -
- “Crude_All.csv” data imported.
- Exploratory Data Analysis - 
  - Dropped useless columns.
  - Added columns derived from “Date” column using add_datepart() from fastai.tabular.
  - Converted the “Date” column to the index of DataFrame.
  - Drop Null/NA/NaN values.
  - Drop values less than or equal to 0 (zero).
  - Aggregate the Initial Close Data to Monthly Frequency and Create a new column “MChange” with percentage change of Average Monthly Close Price.
  - Aggregate the Initial Close Data to Quarterly Frequency and Create a new column “QChange” with percentage change of Average Quarterly Close Price.
  - “GDP.csv” data imported.
  - “Date” is converted to index of GDP DataFrame.
  - New columns “Month” and “Year” are created in GDP DataFrame.
  - Percentage change of GDP is joined with Quarterly Close Price DataFrame.
- Polynomial Regression is Trained, Tested, and Plotted.
- fbProphet is Trained, Tested, and Plotted.

# Model - 3
The model is built using Decision Tree and XGBoost to predict Quarterly and Monthly Returns using previous Quarterly and Monthly Return Price data.

## Approach -
- “Crude_All.csv” data imported.
- Exploratory Data Analysis - 
  - Dropped useless columns.
  - Added columns derived from “Date” column using add_datepart() from fastai.tabular.
  - Converted the “Date” column to the index of DataFrame.
  - Drop Null/NA/NaN values.
  - Drop values less than or equal to 0 (zero).
  - Aggregate the Initial Close Data to Monthly Frequency and Create a new column “MChange” with percentage change of Average Monthly Close Price.
  - Aggregate the Initial Close Data to Quarterly Frequency and Create a new column “QChange” with percentage change of Average Quarterly Close Price.
  - “GDP.csv” data imported.
  - “Date” is converted to index of GDP DataFrame.
  - New columns “Month” and “Year” are created in GDP DataFrame.
  - Percentage change of GDP is joined with Quarterly Close Price DataFrame.
- Decision Tree -
  - The tree is trained using Year, Month, and GDP(Percent change) data and Average Quarterly Return as the dependent variable.
  - The tree is tested using a future 3 quarter prediction.
- XGBoost -
  - XGBoost model is trained using the same parameters as the decision tree and provides a better result while predicting.
