Practical2_Data_Wranggling_2

Create an “Academic performance” dataset of students and perform the following operations using 
Python. 
 
1. Scan all variables for missing values and inconsistencies. If there are missing values and/or 
inconsistencies, use any of the suitable techniques to deal with them.   
2. Scan all numeric variables for outliers. If there are outliers, use any of the suitable 
techniques to deal with them.  
3. Apply data transformations on at least one of the variables. The purpose of this 
transformation should be one of the following reasons: to change the scale for better 
understanding of the variable, to convert a non-linear relation into a linear one, or to 
decrease the skewness and convert the distribution into a normal distribution.  
 
Reason and document your approach properly. 

Code:


import pandas as pd
import numpy as np
from scipy import stats
from sklearn.preprocessing import MinMaxScaler

# Load dataset
df = pd.read_csv("Academic_Performance(1).csv")

# Display first 5 rows
print("First 5 Rows:")
print(df.head())

# Numerical columns
num_cols = ['raisedhands', 'VisITedResources',
            'AnnouncementsView', 'Discussion']

# Categorical columns
cat_cols = ['gender', 'NationalITy', 'PlaceofBirth',
            'StageID', 'GradeID', 'SectionID',
            'Topic', 'Semester', 'Relation',
            'ParentAnsweringSurvey',
            'ParentschoolSatisfaction',
            'StudentAbsenceDays', 'Class']

# Check missing values
print("\nMissing Values:")
print(df.isnull().sum())

# Fill missing values for numerical columns
for col in num_cols:
    df[col] = df[col].fillna(df[col].mean())

# Fill missing values for categorical columns
for col in cat_cols:
    df[col] = df[col].fillna(df[col].mode()[0])

# Convert categorical values to uppercase
for col in cat_cols:
    df[col] = df[col].str.upper()

# Dataset information
print("\nDataset Info:")
print(df.info())

# Statistical summary
print("\nStatistical Summary:")
print(df.describe())

# Detect outliers using Z-score
z_scores = np.abs(stats.zscore(df[num_cols]))

# Display outliers
outliers = df[(z_scores > 3).any(axis=1)]

print("\nOutliers:")
print(outliers)

# Remove outliers
df = df[(z_scores < 3).all(axis=1)].copy()

# Normalize numerical columns
scaler = MinMaxScaler()

df[num_cols] = scaler.fit_transform(df[num_cols])

# Log transformation
for col in num_cols:
    df[col + '_log'] = np.log1p(df[col])

# Final dataset
print("\nFinal Dataset:")
print(df.head())

# Final shape
print("\nFinal Shape:", df.shape)
```

