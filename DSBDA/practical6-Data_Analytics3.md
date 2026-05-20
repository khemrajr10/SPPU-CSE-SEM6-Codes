Practical6_Data_Analytics_III 

1. Implement Simple Naïve Bayes classification algorithm using Python/R on iris.csv dataset. 
2. Compute Confusion matrix to find TP, FP, TN, FN, Accuracy, Error rate, Precision, Recall 
on the given dataset.

Code:

import pandas as pd
import numpy as np

from sklearn.model_selection import train_test_split
from sklearn.preprocessing import LabelEncoder
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import confusion_matrix
from sklearn.metrics import accuracy_score
from sklearn.metrics import precision_score
from sklearn.metrics import recall_score

# Load Dataset
df = pd.read_csv("Iris.csv")

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

# Encode Species Column
label_encoder = LabelEncoder()

df['Species'] = label_encoder.fit_transform(df['Species'])

# Select Features and Target Variable
x = df[['SepalLengthCm',
        'SepalWidthCm',
        'PetalLengthCm',
        'PetalWidthCm']]

y = df['Species']

# Split Dataset into Training and Testing Data
x_train, x_test, y_train, y_test = train_test_split(
    x,
    y,
    test_size=0.25,
    random_state=42
)

# Create Naive Bayes Model
model = GaussianNB()

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

# Accuracy
accuracy = accuracy_score(y_test, y_pred)

print("\nAccuracy")
print(accuracy)

# Error Rate
error_rate = 1 - accuracy

print("\nError Rate")
print(error_rate)

# Precision
precision = precision_score(
    y_test,
    y_pred,
    average='macro'
)

print("\nPrecision")
print(precision)

# Recall
recall = recall_score(
    y_test,
    y_pred,
    average='macro'
)

print("\nRecall")
print(recall)

# Display Labels
print("\nEncoded Species Labels")
print(label_encoder.classes_)
