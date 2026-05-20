Practical5_Data_Analytics2

Data Analytics II 
1. Implement logistic regression using Python/R to perform classification on 
Social_Network_Ads.csv dataset. 
2. Compute Confusion matrix to find TP, FP, TN, FN, Accuracy, Error rate, Precision, Recall 
on the given dataset.

Code:

import pandas as pd
import numpy as np

from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import confusion_matrix
from sklearn.metrics import accuracy_score
from sklearn.metrics import precision_score
from sklearn.metrics import recall_score

# Load Dataset
df = pd.read_csv("Social_Network_Ads.csv")

# Display Dataset
print("First 5 Rows")
print(df.head())

# Shape of Dataset
print("\nShape of Dataset")
print(df.shape)

# Check Missing Values
print("\nMissing Values")
print(df.isnull().sum())

# Dataset Information
print("\nDataset Information")
print(df.info())

# Select Features and Target Variable
x = df[['Age', 'EstimatedSalary']]

y = df['Purchased']

# Split Dataset into Training and Testing Data
x_train, x_test, y_train, y_test = train_test_split(
    x,
    y,
    test_size=0.25,
    random_state=42
)

# Feature Scaling
sc = StandardScaler()

x_train = sc.fit_transform(x_train)

x_test = sc.transform(x_test)

# Create Logistic Regression Model
model = LogisticRegression()

# Train Model
model.fit(x_train, y_train)

# Predict Values
y_pred = model.predict(x_test)

# Display Predicted Values
print("\nPredicted Values")
print(y_pred)

# Create Confusion Matrix
cm = confusion_matrix(y_test, y_pred)

print("\nConfusion Matrix")
print(cm)

# Extract TN, FP, FN, TP
TN = cm[0][0]
FP = cm[0][1]
FN = cm[1][0]
TP = cm[1][1]

print("\nTrue Negative")
print(TN)

print("\nFalse Positive")
print(FP)

print("\nFalse Negative")
print(FN)

print("\nTrue Positive")
print(TP)

# Accuracy
accuracy = accuracy_score(y_test, y_pred)

print("\nAccuracy")
print(accuracy)

# Error Rate
error_rate = 1 - accuracy

print("\nError Rate")
print(error_rate)

# Precision
precision = precision_score(y_test, y_pred)

print("\nPrecision")
print(precision)

# Recall
recall = recall_score(y_test, y_pred)

print("\nRecall")
print(recall)
