Practical 1 Data Wrangling 1
Perform the following operations using Python on any open source dataset (e.g., data.csv) 
1. Import all the required Python Libraries. 
2. Locate an open source data from the web (e.g., https://www.kaggle.com). Provide a clear  
            description of the data and its source (i.e., URL of the web site). 
3. Load the Dataset into pandas dataframe. 
4. Data Preprocessing: check for missing values in the data using pandas isnull(), describe() 
function to get some initial statistics. Provide variable descriptions. Types of variables etc. 
Check the dimensions of the data frame. 
5. Data Formatting and Data Normalization: Summarize the types of variables by checking 
the data types (i.e., character, numeric, integer, factor, and logical) of the variables in the 
data set. If variables are not in the correct data type, apply proper type conversions. 
6. Turn categorical variables into quantitative variables in Python. 
 
In addition to the codes and outputs, explain every operation that you do in the above steps and 
explain everything that you do to import/read/scrape the data set. 

Code:

import pandas as pd
import numpy as np

# Load dataset
df = pd.read_csv("titanic.csv")

# Display dataset
df.head()

# Check missing values
df.isnull().sum()

# Statistical summary
df.describe()

# Dataset information
df.info()

# Shape of dataset
print("Shape:", df.shape)

# Data types
df.dtypes

# Handle missing values
df['Age'] = df['Age'].fillna(df['Age'].mean())

df['Embarked'] = df['Embarked'].fillna(df['Embarked'].mode()[0])

# Check duplicates
df.duplicated().sum()

# Remove duplicates
df = df.drop_duplicates()

# Convert datatypes
df['Survived'] = df['Survived'].astype('category')

df['Sex'] = df['Sex'].astype('category')

df['Embarked'] = df['Embarked'].astype('category')

# Updated datatypes
df.dtypes

# Normalize Age column
df['Age_Normalized'] = (
    (df['Age'] - df['Age'].min()) /
    (df['Age'].max() - df['Age'].min())
)

# Display normalized data
df[['Age', 'Age_Normalized']].head()

# Convert categorical to numerical
df['Sex'] = df['Sex'].map({'male': 0, 'female': 1})

# Final dataset
df.head()

# Final shape
print("Final Shape:", df.shape)


Explanation:
What is Data Wrangling?

Data Wrangling is the process of:

collecting, cleaning ,transforming, organizing raw data into a structured and usable format.

Raw datasets usually contain:

missing values ,duplicate data, incorrect datatypes ,inconsistent values.

Data wrangling prepares the dataset for:
data analysis,visualization, machine learning.
 
It is also called: Data Preprocessing
Process	                   Purpose
Data Collection	        Obtain dataset
Data Cleaning	        Handle missing/incorrect data
Data Transformation	Modify data format
Data Integration	Combine datasets
Data Reduction	        Remove unnecessary data
Data Normalization	Scale numerical values
Encoding	        Convert categorical to numerical
Duplicate Removal	Remove repeated rows

Pandas (pd)

Pandas is a Python library used for:
data manipulation,
analysis,
handling tables.
It provides: DataFrame, Series
structures for working with datasets.

NumPy (np)

NumPy is a numerical computing library used for:
mathematical operations, arrays, numerical calculations.
Although not heavily used here, it is commonly imported in data analysis projects.

What is a DataFrame?

A DataFrame is:
a tabular structure,
similar to an Excel sheet or SQL table.
It contains:
rows
columns

head()
Displays the first 5 rows of the dataset.
Purpose:
quickly inspect data,
verify dataset loaded correctly.

isnull()
Checks whether each value is missing (NULL/NaN).
Returns:
True for missing values
False otherwise

sum()
Counts total missing values column-wise.

Example
Column	Missing Values
Age	177
Cabin	687

Why Missing Values Matter
Missing data can:
reduce accuracy,
create errors,
affect analysis.
Therefore they must be:
filled,
removed,
or handled properly.
Generates statistical summary for numerical columns.
Statistics Produced

Statistic	Meaning
count	Number of non-null values
mean	Average
std	Standard deviation
min	Minimum value
25%	First quartile
50%	Median
75%	Third quartile
max	Maximum value
Why It Is Important

Helps understand:
data distribution,
spread,
central tendency,
outliers.

What is Normalization?
Normalization scales numerical values into a fixed range: 0 to 1
formula:
Xnorm​= (X - Xmin)/ (Xmax - Xmin)

Why Normalization Is Important
Different columns may have different scales.
Example:
Age: 0–80
Fare: 0–500
Large values may dominate analysis.
Normalization:
standardizes scale,
improves machine learning performance.




Code 2:

# Import Libraries
import numpy as np
import pandas as pd

# Titanic Dataset
# Source:
# https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv
#
# Description:
# The Titanic dataset contains passenger details such as
# PassengerId, Survived status, Passenger Class, Name, Sex,
# Age, Fare, Embarked location etc.
# This dataset is commonly used for data preprocessing
# and machine learning tasks.

# Load Dataset from URL
df = pd.read_csv(
    "https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv"
)

# Display Dataset
df.head()
df.tail()

# Shape of Dataset
df.shape

# Statistical Summary
df.describe()

# Check Missing Values
df.isnull()
df.isnull().any()
df.isnull().sum()

# Check Datatypes
df.dtypes

# Convert Datatypes
df['Survived'] = df['Survived'].astype('category')
df['Sex'] = df['Sex'].astype('category')
df['Embarked'] = df['Embarked'].astype('category')

# Updated Datatypes
df.dtypes

# Fill Missing Values
df['Age'] = df['Age'].fillna(df['Age'].mean())

df['Embarked'] = df['Embarked'].fillna(df['Embarked'].mode()[0])

# Check Duplicate Values
df.duplicated().sum()

# Remove Duplicate Values
df = df.drop_duplicates()

# Data Normalization
from sklearn import preprocessing

minmax = preprocessing.MinMaxScaler()

# Selecting Numerical Columns
x = df[['Age', 'Fare']]

# Normalize Data
x_scaled = minmax.fit_transform(x)

# Create Normalized DataFrame
df_normalized = pd.DataFrame(
    x_scaled,
    columns=['Age_Normalized', 'Fare_Normalized']
)

# Display Normalized Data
df_normalized

# Convert Categorical Variables into Numerical Variables
label_encoder = preprocessing.LabelEncoder()

df['Sex'] = label_encoder.fit_transform(df['Sex'])

df['Embarked'] = label_encoder.fit_transform(df['Embarked'])

# Display Unique Encoded Values
df['Sex'].unique()
df['Embarked'].unique()

# Final Dataset
df.head()


Explanation:
Import Preprocessing Module
from sklearn import preprocessing
Used for:
normalization
encoding
scaling

Min-Max Normalization is a data preprocessing technique used in Machine Learning.
Its purpose is to bring all numerical values into the same range, usually between: 0 and 1

Why Do We Need Normalization?
In datasets, some columns may have:
very small values
very large values
Example:
Age	Fare
22	7.25
38	71.28
80	512.32
Here:
Age values are small
Fare values are much larger
If we directly give this to machine learning algorithms:
large-value columns dominate calculations
model becomes biased
So we normalize data.

Apply Normalization
x_scaled = minmax.fit_transform(x)
fit_transform()
fit:
Learns:minimum value & maximum value

transform: Applies normalization.

What is Label Encoding?
Converts text labels into numbers.
Example:
Male/Female	Encoded
male	1
female	0

Encode Sex Column
df['Sex'] = label_encoder.fit_transform(df['Sex'])
Converts:
male → 1
female → 0
Machine learning requires numeric data.

Encode Embarked Column
df['Embarked'] = label_encoder.fit_transform(df['Embarked'])
Example:
Port	Encoded
C	0
Q	1
S	2
