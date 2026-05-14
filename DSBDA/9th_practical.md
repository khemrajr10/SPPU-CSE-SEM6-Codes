ractical9_Data_Visualization2

Use the inbuilt dataset 'titanic' as used in the above problem. Plot a box plot for distribution 
of age with respect to each gender along with the information about whether they survived 
or not. (Column names : 'sex' and 'age') 
2. Write observations on the inference from the above statistics. 

Code:

import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Load Titanic Dataset
df = sns.load_dataset('titanic')

# Display First 5 Rows
print("First 5 Rows")
print(df.head())

# Shape of Dataset
print("\nShape of Dataset")
print(df.shape)

# Dataset Information
print("\nDataset Information")
print(df.info())

# Check Missing Values
print("\nMissing Values")
print(df.isnull().sum())

# Statistical Summary
print("\nStatistical Summary")
print(df.describe())

# Box Plot for Age Distribution
plt.figure(figsize=(8,6))

sns.boxplot(
    x='sex',
    y='age',
    hue='survived',
    data=df
)

plt.title("Age Distribution with Gender and Survival Status")

plt.xlabel("Gender")

plt.ylabel("Age")

plt.show()



Other Plot may be asked:

import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Load Titanic Dataset
df = sns.load_dataset('titanic')

# Display First 5 Rows
print("First 5 Rows")
print(df.head())

# Shape of Dataset
print("\nShape of Dataset")
print(df.shape)

# Dataset Information
print("\nDataset Information")
print(df.info())

# Check Missing Values
print("\nMissing Values")
print(df.isnull().sum())

# Statistical Summary
print("\nStatistical Summary")
print(df.describe())

# 1. Histogram - Fare Distribution
plt.figure(figsize=(8,5))

sns.histplot(df['fare'])

plt.title("Fare Distribution")

plt.xlabel("Fare")

plt.ylabel("Frequency")

plt.show()

# 2. Count Plot - Gender Distribution
plt.figure(figsize=(6,5))

sns.countplot(
    x='sex',
    data=df
)

plt.title("Gender Distribution")

plt.xlabel("Gender")

plt.ylabel("Passenger Count")

plt.show()

# 3. Bar Plot - Average Fare by Class
plt.figure(figsize=(6,5))

sns.barplot(
    x='class',
    y='fare',
    data=df
)

plt.title("Average Fare by Passenger Class")

plt.xlabel("Passenger Class")

plt.ylabel("Average Fare")

plt.show()

# 4. Box Plot - Age Distribution by Gender
plt.figure(figsize=(8,6))

sns.boxplot(
    x='sex',
    y='age',
    data=df
)

plt.title("Age Distribution by Gender")

plt.xlabel("Gender")

plt.ylabel("Age")

plt.show()

# 5. Violin Plot - Age Distribution
plt.figure(figsize=(8,6))

sns.violinplot(
    x='sex',
    y='age',
    data=df
)

plt.title("Violin Plot of Age Distribution")

plt.xlabel("Gender")

plt.ylabel("Age")

plt.show()

# 6. Scatter Plot - Age vs Fare
plt.figure(figsize=(8,6))

sns.scatterplot(
    x='age',
    y='fare',
    data=df
)

plt.title("Age vs Fare")

plt.xlabel("Age")

plt.ylabel("Fare")

plt.show()

# 7. Line Plot - Age vs Fare
plt.figure(figsize=(8,6))

sns.lineplot(
    x='age',
    y='fare',
    data=df
)

plt.title("Line Plot of Age and Fare")

plt.xlabel("Age")

plt.ylabel("Fare")

plt.show()

# 8. Heatmap - Correlation Matrix
plt.figure(figsize=(8,6))

sns.heatmap(
    df.corr(numeric_only=True),
    annot=True
)

plt.title("Correlation Heatmap")

plt.show()

# 9. Pair Plot
sns.pairplot(df)

plt.show()

# 10. KDE Plot - Age Density
plt.figure(figsize=(8,5))

sns.kdeplot(df['age'])

plt.title("KDE Plot of Age")

plt.xlabel("Age")

plt.show()

# 11. Joint Plot - Age and Fare
sns.jointplot(
    x='age',
    y='fare',
    data=df
)

plt.show()

# 12. Swarm Plot - Fare by Class
plt.figure(figsize=(8,6))

sns.swarmplot(
    x='class',
    y='fare',
    data=df
)

plt.title("Swarm Plot of Fare by Class")

plt.xlabel("Passenger Class")

plt.ylabel("Fare")

plt.show()

# 13. Strip Plot - Fare Distribution by Class
plt.figure(figsize=(8,6))

sns.stripplot(
    x='class',
    y='fare',
    data=df
)

plt.title("Strip Plot of Fare by Class")

plt.xlabel("Passenger Class")

plt.ylabel("Fare")

plt.show()

# 14. Regression Plot - Age vs Fare
plt.figure(figsize=(8,6))

sns.regplot(
    x='age',
    y='fare',
    data=df
)

plt.title("Regression Plot of Age vs Fare")

plt.xlabel("Age")

plt.ylabel("Fare")

plt.show()


Explanation:

1. What is the objective of this practical?

The objective of this practical is to visualize the distribution of passenger age with respect to gender and survival status using a Box Plot.

2. Which dataset is used in this practical?

The Titanic Dataset is used.

It contains information about Titanic passengers such as:

age
gender
class
fare
survival status
3. Which libraries are used?
Library	Purpose
pandas	Data handling
Seaborn	Statistical visualization
Matplotlib	Plot creation and customization
4. Explain this code.
import pandas as pd

Imports pandas library and assigns alias:

pd
5. Why is pandas used?

Pandas is used for:

dataset handling
DataFrame operations
preprocessing and analysis
6. Explain this code.
import seaborn as sns

Imports Seaborn library with alias:

sns
7. Why is Seaborn used?

Seaborn is used for:

attractive graphs
statistical visualization
easier plotting
8. Explain this code.
import matplotlib.pyplot as plt

Imports pyplot module from Matplotlib.

Alias used:

plt
9. Why is Matplotlib used?

Matplotlib is used for:

creating figures
labeling graphs
displaying plots
10. Explain this code.
df = sns.load_dataset('titanic')

Loads inbuilt Titanic dataset from Seaborn.

11. What is stored in df?
df

stores Titanic dataset in DataFrame format.

12. Explain this code.
print(df.head())

Displays first 5 rows of dataset.

13. Why is head() used?

head() is used to:

preview data
understand structure
verify dataset loading
14. Explain this code.
df.shape

Returns dimensions of dataset.

15. What does shape represent?
(rows, columns)

Example:

(891, 15)

means:

891 rows
15 columns
16. Explain this code.
df.info()

Displays:

column names
datatypes
non-null values
memory usage
17. Why is info() important?

It helps identify:

missing values
datatypes
dataset structure
18. Explain this code.
df.isnull().sum()

Checks missing values in each column.

19. What are missing values?

Missing values are unavailable/empty values represented as:

NaN
20. Why are missing values checked?

Missing values can:

affect visualization
reduce model accuracy
create incorrect analysis
21. Explain this code.
df.describe()

Provides statistical summary of numerical columns.

22. What statistics does describe() provide?

It provides:

count
mean
standard deviation
minimum
maximum
quartiles
23. What is a Box Plot?

A Box Plot is a statistical graph used to show:

distribution of data
median
quartiles
outliers
spread of data
24. Why is box plot used in this practical?

Box plot helps compare:

age distribution
gender differences
survival patterns
outliers
25. Explain this code.
plt.figure(figsize=(8,6))

Creates new graph figure.

26. What does figsize=(8,6) mean?
Value	Meaning
8	Width
6	Height

Unit:

Inches
27. Why is figure size used?

Figure size improves:

readability
graph appearance
spacing
28. Explain this code.
sns.boxplot(
    x='sex',
    y='age',
    hue='survived',
    data=df
)

Creates box plot using:

gender
age
survival status
29. What does x='sex' mean?

Places:

Gender

on X-axis.

Categories:

male
female
30. What does y='age' mean?

Places:

Age

on Y-axis.

31. What does hue='survived' mean?

Separates data based on:

Survival Status

Values:

0 → Did not survive
1 → Survived

Different colors represent different survival categories.

32. Why is hue used?

hue helps compare multiple categories within same graph.

33. What does data=df mean?

Uses:

df DataFrame

for plotting.

34. What does this box plot show?

This box plot shows:

age distribution by gender
survival comparison
spread of age
outliers
median age
35. How do you read box plot?
Part	Meaning
Middle Line	Median
Box	Interquartile Range
Whiskers	Data spread
Dots outside whiskers	Outliers
36. What is median?

Median is middle value of ordered dataset.

37. What is Interquartile Range (IQR)?

IQR represents middle 50% of data.

Formula:

IQR = Q3 - Q1

Where:

Q1 = 25th percentile
Q3 = 75th percentile
38. What are whiskers?

Whiskers are lines extending from box showing spread of normal data excluding outliers.

39. What are outliers?

Outliers are unusually high or low values lying outside whiskers.

40. How are outliers detected?

Outliers are values outside:

Q1 - 1.5 × IQR

and

Q3 + 1.5 × IQR
41. Explain this code.
plt.title("Age Distribution with Gender and Survival Status")

Adds title to graph.

42. Why is title important?

Title explains:

purpose of graph
what visualization represents
43. Explain this code.
plt.xlabel("Gender")

Adds label to X-axis.

44. Explain this code.
plt.ylabel("Age")

Adds label to Y-axis.

45. Explain this code.
plt.show()

Displays graph output.

46. What observations can be made from this plot?

Possible observations:

female passengers had better survival rate
age distribution differs between genders
outliers exist in passenger ages
younger females survived more frequently
47. Why is box plot better than histogram here?

Because box plot:

compares multiple categories together
detects outliers easily
shows median and spread clearly
48. What is the final conclusion of this practical?

This practical visualizes passenger age distribution with respect to gender and survival status using box plot and helps analyze:

median age
spread of data
outliers
survival patterns.



Plot		Example							Purpose
Histogram	sns.histplot(df['fare'])			Distribution of numerical data
Count Plot	sns.countplot(x='sex', data=df)			Frequency of categorical data
Bar Plot	sns.barplot(x='class', y='fare', data=df)	Compare averages
Box Plot	sns.boxplot(x='sex', y='age', data=df)		Outlier detection and spread
Violin Plot	sns.violinplot(x='sex', y='age', data=df)	Distribution + density
Scatter Plot	sns.scatterplot(x='age', y='fare', data=df)	Relationship between variables
Line Plot	sns.lineplot(x='age', y='fare', data=df)	Trend analysis
Pair Plot	sns.pairplot(df)				Relationship among multiple variables
Heatmap		sns.heatmap(df.corr(), annot=True)		Correlation analysis
KDE Plot	sns.kdeplot(df['age'])				Probability density distribution
Joint Plot	sns.jointplot(x='age', y='fare', data=df)	Scatter + distributions
Swarm Plot	sns.swarmplot(x='class', y='fare', data=df)	Individual data points
Strip Plot	sns.stripplot(x='class', y='fare', data=df)	Data point distribution
Pie Chart	plt.pie()	Percentage distribution
Area Plot	df.plot.area()	Cumulative trends
Regression Plot	sns.regplot(x='age', y='fare', data=df)	Regression relationship
