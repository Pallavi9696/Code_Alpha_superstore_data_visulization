# Code_Alpha_superstore_data_visulization
Data Visualization Project
Description

This project demonstrates data visualization techniques using Python (Matplotlib & Seaborn).
The goal is to transform raw data into clear, insightful, and compelling visuals that help in understanding patterns, trends, and relationships in the dataset.

# Task 2
# Data Visualization Project
# Dataset: Sample - Superstore.csv sales datasets

# Step 1: Import Libraries




```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

# Step 2: Load Dataset


```python
file_path = "archive (2).csv"   # make sure the file is in the same directory
df = pd.read_csv(file_path)
```

# Step 3: Explore Data Structure


```python
print("Shape of dataset:", df.shape)
print("\nDataset Info:\n")
df.info()
print("\nMissing Values:\n", df.isnull().sum())
print("\nDuplicate Rows:", df.duplicated().sum())
print("\nStatistical Summary (Numerical):\n", df.describe())
print("\nStatistical Summary (Categorical):\n", df.describe(include='object'))
```

    Shape of dataset: (9994, 21)
    
    Dataset Info:
    
    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 9994 entries, 0 to 9993
    Data columns (total 21 columns):
     #   Column         Non-Null Count  Dtype  
    ---  ------         --------------  -----  
     0   Row ID         9994 non-null   int64  
     1   Order ID       9994 non-null   object 
     2   Order Date     9994 non-null   object 
     3   Ship Date      9994 non-null   object 
     4   Ship Mode      9994 non-null   object 
     5   Customer ID    9994 non-null   object 
     6   Customer Name  9994 non-null   object 
     7   Segment        9994 non-null   object 
     8   Country        9994 non-null   object 
     9   City           9994 non-null   object 
     10  State          9994 non-null   object 
     11  Postal Code    9994 non-null   int64  
     12  Region         9994 non-null   object 
     13  Product ID     9994 non-null   object 
     14  Category       9994 non-null   object 
     15  Sub-Category   9994 non-null   object 
     16  Product Name   9994 non-null   object 
     17  Sales          9994 non-null   float64
     18  Quantity       9994 non-null   int64  
     19  Discount       9994 non-null   float64
     20  Profit         9994 non-null   float64
    dtypes: float64(3), int64(3), object(15)
    memory usage: 1.6+ MB
    
    Missing Values:
     Row ID           0
    Order ID         0
    Order Date       0
    Ship Date        0
    Ship Mode        0
    Customer ID      0
    Customer Name    0
    Segment          0
    Country          0
    City             0
    State            0
    Postal Code      0
    Region           0
    Product ID       0
    Category         0
    Sub-Category     0
    Product Name     0
    Sales            0
    Quantity         0
    Discount         0
    Profit           0
    dtype: int64
    
    Duplicate Rows: 0
    
    Statistical Summary (Numerical):
                 Row ID   Postal Code         Sales     Quantity     Discount  \
    count  9994.000000   9994.000000   9994.000000  9994.000000  9994.000000   
    mean   4997.500000  55190.379428    229.858001     3.789574     0.156203   
    std    2885.163629  32063.693350    623.245101     2.225110     0.206452   
    min       1.000000   1040.000000      0.444000     1.000000     0.000000   
    25%    2499.250000  23223.000000     17.280000     2.000000     0.000000   
    50%    4997.500000  56430.500000     54.490000     3.000000     0.200000   
    75%    7495.750000  90008.000000    209.940000     5.000000     0.200000   
    max    9994.000000  99301.000000  22638.480000    14.000000     0.800000   
    
                Profit  
    count  9994.000000  
    mean     28.656896  
    std     234.260108  
    min   -6599.978000  
    25%       1.728750  
    50%       8.666500  
    75%      29.364000  
    max    8399.976000  
    
    Statistical Summary (Categorical):
                   Order ID Order Date   Ship Date       Ship Mode Customer ID  \
    count             9994       9994        9994            9994        9994   
    unique            5009       1237        1334               4         793   
    top     CA-2017-100111   9/5/2016  12/16/2015  Standard Class    WB-21850   
    freq                14         38          35            5968          37   
    
            Customer Name   Segment        Country           City       State  \
    count            9994      9994           9994           9994        9994   
    unique            793         3              1            531          49   
    top     William Brown  Consumer  United States  New York City  California   
    freq               37      5191           9994            915        2001   
    
           Region       Product ID         Category Sub-Category     Product Name  
    count    9994             9994             9994         9994             9994  
    unique      4             1862                3           17             1850  
    top      West  OFF-PA-10001970  Office Supplies      Binders  Staple envelope  
    freq     3203               19             6026         1523               48  
    

# Step 4: Unique Values per Column


```python
print("\nUnique values per column:\n")
for col in df.columns:
    print(f"{col}: {df[col].nunique()} unique values")

```

    
    Unique values per column:
    
    Row ID: 9994 unique values
    Order ID: 5009 unique values
    Order Date: 1237 unique values
    Ship Date: 1334 unique values
    Ship Mode: 4 unique values
    Customer ID: 793 unique values
    Customer Name: 793 unique values
    Segment: 3 unique values
    Country: 1 unique values
    City: 531 unique values
    State: 49 unique values
    Postal Code: 631 unique values
    Region: 4 unique values
    Product ID: 1862 unique values
    Category: 3 unique values
    Sub-Category: 17 unique values
    Product Name: 1850 unique values
    Sales: 5825 unique values
    Quantity: 14 unique values
    Discount: 12 unique values
    Profit: 7287 unique values
    

# Step 5: Numerical Features Distribution


```python
num_cols = df.select_dtypes(include=np.number).columns
for col in num_cols:
    plt.figure(figsize=(6,4))
    sns.histplot(df[col], bins=40, kde=True)
    plt.title(f"Distribution of {col}")
    plt.show()
```


    
![png](output_10_0.png)
    



    
![png](output_10_1.png)
    



    
![png](output_10_2.png)
    



    
![png](output_10_3.png)
    



    
![png](output_10_4.png)
    



    
![png](output_10_5.png)
    




# Step 6: Categorical Features Count Plots


```python
def plot_top_categories(df, column, n=10):
    """Plots the count of the top N categories in a column."""
    top_categories = df[column].value_counts().nlargest(n).index
    df_filtered = df[df[column].isin(top_categories)]
    plt.figure(figsize=(15, 8))
    sns.countplot(x=column, data=df_filtered, order=top_categories)
    plt.title(f"Count of Top {n} {column}")
    plt.xticks(rotation=90)
    plt.show()
```

Now I will use this function to plot the top 10 categories for each categorical column.


```python
cat_cols = df.select_dtypes(include='object').columns
for col in cat_cols:
    # Exclude columns with too many unique values that would still be congested
    if df[col].nunique() <= 50: # You can adjust this threshold
        plot_top_categories(df, col, n=10)
    else:
        print(f"Skipping plotting for {col} as it has too many unique values.")
```

    Skipping plotting for Order ID as it has too many unique values.
    Skipping plotting for Order Date as it has too many unique values.
    Skipping plotting for Ship Date as it has too many unique values.
    


    
![png](output_15_1.png)
    


    Skipping plotting for Customer ID as it has too many unique values.
    Skipping plotting for Customer Name as it has too many unique values.
    


    
![png](output_15_3.png)
    



    
![png](output_15_4.png)
    


    Skipping plotting for City as it has too many unique values.
    


    
![png](output_15_6.png)
    



    
![png](output_15_7.png)
    


    Skipping plotting for Product ID as it has too many unique values.
    


    
![png](output_15_9.png)
    



    
![png](output_15_10.png)
    


    Skipping plotting for Product Name as it has too many unique values.
    


```python
plt.figure(figsize=(10, 6))
sns.barplot(x='Category', y='Sales', data=df)
plt.title('Average Sales by Category')
plt.show()
```


    
![png](output_16_0.png)
    


# Step 7: Correlation Analysis (Numerical Variables)


```python
plt.figure(figsize=(10,6))
numerical_df = df.select_dtypes(include=np.number) # Select only numerical columns
sns.heatmap(numerical_df.corr(), annot=True, cmap="coolwarm", fmt=".2f") # Compute correlation on numerical data
plt.title("Correlation Heatmap of Numerical Variables")
plt.show()
```


    
![png](output_18_0.png)
    


# Step 8: Boxplots for Outliers & Category vs Price


```python
numerical_cols_for_boxplot = ['Sales', 'Profit']
for num_col in numerical_cols_for_boxplot:
    for col in cat_cols:
        # Exclude columns with too many unique values that would still be congested for boxplots
        if df[col].nunique() <= 20: # Adjusted threshold for boxplots
            plt.figure(figsize=(12, 6))
            sns.boxplot(x=col, y=num_col, data=df)
            plt.title(f"{num_col} Distribution by {col}")
            plt.xticks(rotation=45)
            plt.show()
        else:
            print(f"Skipping boxplot for {num_col} by {col} as it has too many unique values for a clear boxplot.")
```

    Skipping boxplot for Sales by Order ID as it has too many unique values for a clear boxplot.
    Skipping boxplot for Sales by Order Date as it has too many unique values for a clear boxplot.
    Skipping boxplot for Sales by Ship Date as it has too many unique values for a clear boxplot.
    


    
![png](output_20_1.png)
    


    Skipping boxplot for Sales by Customer ID as it has too many unique values for a clear boxplot.
    Skipping boxplot for Sales by Customer Name as it has too many unique values for a clear boxplot.
    


    
![png](output_20_3.png)
    



    
![png](output_20_4.png)
    


    Skipping boxplot for Sales by City as it has too many unique values for a clear boxplot.
    Skipping boxplot for Sales by State as it has too many unique values for a clear boxplot.
    


    
![png](output_20_6.png)
    


    Skipping boxplot for Sales by Product ID as it has too many unique values for a clear boxplot.
    


    
![png](output_20_8.png)
    



    
![png](output_20_9.png)
    


    Skipping boxplot for Sales by Product Name as it has too many unique values for a clear boxplot.
    Skipping boxplot for Profit by Order ID as it has too many unique values for a clear boxplot.
    Skipping boxplot for Profit by Order Date as it has too many unique values for a clear boxplot.
    Skipping boxplot for Profit by Ship Date as it has too many unique values for a clear boxplot.
    


    
![png](output_20_11.png)
    


    Skipping boxplot for Profit by Customer ID as it has too many unique values for a clear boxplot.
    Skipping boxplot for Profit by Customer Name as it has too many unique values for a clear boxplot.
    


    
![png](output_20_13.png)
    



    
![png](output_20_14.png)
    


    Skipping boxplot for Profit by City as it has too many unique values for a clear boxplot.
    Skipping boxplot for Profit by State as it has too many unique values for a clear boxplot.
    


    
![png](output_20_16.png)
    


    Skipping boxplot for Profit by Product ID as it has too many unique values for a clear boxplot.
    


    
![png](output_20_18.png)
    



    
![png](output_20_19.png)
    


    Skipping boxplot for Profit by Product Name as it has too many unique values for a clear boxplot.
    

# Step 9: Trends / Patterns Example


```python
plt.figure(figsize=(10, 6))
sns.barplot(x='Category', y='Sales', data=df)
plt.title('Average Sales by Category')
plt.show()
```


    
![png](output_22_0.png)
    



```python
numerical_cols_for_boxplot = ['Sales', 'Profit']
for num_col in numerical_cols_for_boxplot:
    plt.figure(figsize=(12, 6))
    sns.boxplot(x='Category', y=num_col, data=df)
    plt.title(f"{num_col} Distribution by Category")
    plt.xticks(rotation=45)
    plt.show()
```


    
![png](output_23_0.png)
    



    
![png](output_23_1.png)
    



```python

```
