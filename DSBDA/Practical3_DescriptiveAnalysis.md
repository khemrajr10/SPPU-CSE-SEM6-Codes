Practical_3_Descriptive Statistics

 Descriptive Statistics - Measures of Central Tendency and variability 
Perform the following operations on any open source dataset (e.g., data.csv) 
1. Provide summary statistics (mean, median, minimum, maximum, standard deviation) for 
a dataset (age, income etc.) with numeric variables grouped by one of the qualitative 
(categorical) variable. For example, if your categorical variable is age groups and 
quantitative variable is income, then provide summary statistics of income grouped by the 
age groups. Create a list that contains a numeric value for each response to the categorical 
variable.  
2. Write a Python program to display some basic statistical details like percentile, mean, 
standard deviation etc. of the species of ‘Iris-setosa’, ‘Iris-versicolor’ and ‘Iris-versicolor’ 
of iris.csv dataset. 
 
 Provide the codes with outputs and explain everything that you do in this step. 

Code:

import pandas as pd
import numpy as np

# Load Dataset
df = pd.read_csv("Iris.csv")

# Display Dataset
print("First 5 Rows")
print(df.head())

# Group Sepal Length by Species
grouped_data = df.groupby('Species')['SepalLengthCm']

# Mean
print("\n")
print("MEAN")
print(grouped_data.mean())

# Median
print("\n")
print("MEDIAN")
print(grouped_data.median())

# Minimum
print("\n")
print("MINIMUM")
print(grouped_data.min())

# Maximum
print("\n")
print("MAXIMUM")
print(grouped_data.max())

# Standard Deviation
print("\n")
print("STANDARD DEVIATION")
print(grouped_data.std())

# List of Numeric Values
print("\n")
print("LIST OF VALUES")
print(grouped_data.apply(list))

# Separate Species
setosa = df[df['Species'] == 'Iris-setosa']

versicolor = df[df['Species'] == 'Iris-versicolor']

virginica = df[df['Species'] == 'Iris-virginica']

# Function for Statistics
def statistics(species_data, species_name):

    print("\n")   
    print("Statistics for:", species_name)
    

    print("\nMean")
    print(species_data.mean(numeric_only=True))

    print("\nMedian")
    print(species_data.median(numeric_only=True))

    print("\nStandard Deviation")
    print(species_data.std(numeric_only=True))

    print("\nPercentiles")
    print(
        species_data.quantile(
            [0.25, 0.50, 0.75],
            numeric_only=True
        )
    )

    print("\nMinimum")
    print(species_data.min(numeric_only=True))

    print("\nMaximum")
    print(species_data.max(numeric_only=True))

# Call Function
statistics(setosa, 'Iris-setosa')

statistics(versicolor, 'Iris-versicolor')

statistics(virginica, 'Iris-virginica')


