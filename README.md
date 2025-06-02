# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
df = pd.read_csv("/content/titanic_dataset .csv")  # Replace with actual path

# Display basic info
df.info()

# Display first few rows
df.head()

# Check shape
print(f"Dataset contains {df.shape[0]} rows and {df.shape[1]} columns")
```
![Screenshot 2025-03-24 162352](https://github.com/user-attachments/assets/abb9bdbf-7e6d-4d6e-8f50-94041b537896)

```
# Set PassengerId as index
df.set_index("PassengerId", inplace=True)

# Summary statistics
df.describe()
```
![Screenshot 2025-03-24 162356](https://github.com/user-attachments/assets/c46f9118-92b9-4369-9c9e-29b2ed2bc028)


```
# Count unique values in categorical columns
categorical_columns = ["Survived", "Pclass", "Sex", "Embarked"]
for col in categorical_columns:
    print(f"{col} unique values:\n", df[col].value_counts(), "\n")
```
![Screenshot 2025-03-24 162401](https://github.com/user-attachments/assets/e655fb42-f7d4-4694-b78d-4d0b8c5074de)


```
sns.countplot(data=df, x="Survived")
plt.title("Survival Count")
plt.show()
```
![Screenshot 2025-03-24 162404](https://github.com/user-attachments/assets/d4351711-9356-4077-94cd-0e566293b1da)


```
df["Pclass"].unique()
```
![Screenshot 2025-03-24 162411](https://github.com/user-attachments/assets/2fde3a32-da69-4579-9cfa-56e2e858033d)


```
df.rename(columns={"Sex": "Gender"}, inplace=True)
```
```
sns.catplot(x='Survived', hue='Gender', data=df, kind='count')
plt.title("Survival by Gender")
plt.show()
```
![Screenshot 2025-03-24 162418](https://github.com/user-attachments/assets/bb38b658-b9ef-456b-92db-107f6831a420)


```
sns.boxplot(x="Survived", y="Age", data=df)
plt.title("Age Distribution by Survival")
plt.show()
```
![Screenshot 2025-03-24 162423](https://github.com/user-attachments/assets/b8cbf635-3113-408a-a7a1-c8c7084bc9d0)

```
sns.boxplot(x="Pclass", y="Age", hue="Gender", data=df)
plt.title("Age Distribution Across Passenger Classes and Gender")
plt.show()
```
![Screenshot 2025-03-24 162428](https://github.com/user-attachments/assets/0288b04a-b650-48cf-84eb-c6d826b7e987)


```

sns.catplot(x="Pclass", y="Survived", hue="Gender", data=df, kind="bar")
plt.title("Survival Rate by Passenger Class and Gender")
plt.show()
```
![Screenshot 2025-03-24 162432](https://github.com/user-attachments/assets/b7a55d48-333d-48bb-9a2d-227401886569)


```

plt.figure(figsize=(10,6))

# Select only numerical columns
numerical_df = df.select_dtypes(include=["number"])

# Compute correlation and plot heatmap
sns.heatmap(numerical_df.corr(), annot=True, cmap="coolwarm", fmt=".2f")
plt.title("Feature Correlation Heatmap")
plt.show()

```
![Screenshot 2025-03-24 162448](https://github.com/user-attachments/assets/3b55d0b6-2125-4da4-8f49-ac1901c94c2d)


```

sns.pairplot(df, hue="Survived", diag_kind="kde")
plt.show()

```
11


# RESULT
 Thus, the Exploratory Data Analysis on the given data set was performed successfully.      
