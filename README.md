# Soil Moisture Trend Analysis

This repository features a cleaned dataset of soil moisture sensor readings. By removing noise and outliers from the raw sensor data, we can accurately model moisture trends over time using linear regression.

## 📊 Dataset Overview
The dataset focuses on the relationship between time and sensor output.

### Key Features:
* **Timestamp:** Standardized date and time of the reading.
* **Sensor_Reading:** The cleaned numerical value from the soil moisture sensor.

## 🛠️ Data Cleaning & Analysis
The data underwent the following processing steps:
1.  **Noise Reduction:** Removed erratic spikes from the raw sensor feed.
2.  **Normalization:** Scaled readings for consistent analysis.
3.  **Linear Regression:** Applied a linear model to visualize the rate of soil drying or saturation over the recorded period.

## 📂 File Structure
* `soil_moisture_cleaned.csv`: The processed data file.


## 🚀 Visualization
Using this cleaned data, we can generate a linear regression graph to observe the moisture trend:

```python
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.linear_model import LinearRegression
import numpy as np

# Load data
df = pd.read_csv('soil_moisture_cleaned.csv')
df['Timestamp'] = pd.to_datetime(df['Timestamp'])

# Convert time to a numerical value for regression (e.g., days since start)
df['Time_Delta'] = (df['Timestamp'] - df['Timestamp'].min()).dt.total_seconds()

X = df[['Time_Delta']]
y = df['Sensor_Reading']

# Fit Linear Regression
model = LinearRegression().fit(X, y)
prediction = model.predict(X)

# Plotting
plt.scatter(df['Timestamp'], y, color='blue', label='Cleaned Data', s=10)
plt.plot(df['Timestamp'], prediction, color='red', label='Linear Trend')
plt.xlabel('Time')
plt.ylabel('Moisture Reading')
plt.legend()
plt.show()
kfhfhioeutrouetwoiefjknvmccxvhgioeroitweyutwuetoiewuljfkjdklfheifhioewutoieutowutopqeupotuopetuopew
