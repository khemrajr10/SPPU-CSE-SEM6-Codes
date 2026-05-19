Practical_4_Data_AnalyticsI

Create a Linear Regression Model using Python/R to predict home prices using Boston Housing 
Dataset (https://www.kaggle.com/c/boston-housing). The Boston Housing dataset contains 
information about various houses in Boston through different parameters. There are 506 samples 
and 14 feature variables in this dataset.  
 
The objective is to predict the value of prices of the house using the given features.

Code:

import pandas as pd
import numpy as np

from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score

# Load Dataset
df = pd.read_csv("BostonHousing.csv")

# Display Dataset
print("First 5 Rows")
print(df.head())

# Shape of Dataset
print("\nShape of Dataset")
print(df.shape)

# Check Missing Values
print("\nMissing Values")
print(df.isnull().sum())

# Fill Missing Values
df = df.fillna(df.mean(numeric_only=True))

# Dataset Information
print("\nDataset Information")
print(df.info())

# Statistical Summary
print("\nStatistical Summary")
print(df.describe())

# Define Features and Target Variable
x = df.drop('medv', axis=1)

y = df['medv']

# Split Dataset into Training and Testing Data
x_train, x_test, y_train, y_test = train_test_split(
    x,
    y,
    test_size=0.2,
    random_state=42
)

# Create Linear Regression Model
model = LinearRegression()

# Train Model
model.fit(x_train, y_train)

# Predict House Prices
y_pred = model.predict(x_test)

# Display Predicted Values
print("\nPredicted House Prices")
print(y_pred[:10])

# Model Evaluation
mse = mean_squared_error(y_test, y_pred)

r2 = r2_score(y_test, y_pred)

print("\nMean Squared Error")
print(mse)

print("\nR2 Score")
print(r2)
