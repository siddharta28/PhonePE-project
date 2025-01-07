# PhonePe Digital Payments Case Study [(Click Here To Watch)](https://colab.research.google.com/drive/192_g4epsvA16JFA1HbhEoGRXfJrNZIeB?usp=drive_link)
---
Analyzed 10K+ PhonePe records, uncovering trends in transactions and regional performance through 15+ visualizations with Python (Pandas, NumPy, Matplotlib, Seaborn).

## Table of Contents
- [Project Overview](#Project-Overview)
- [Key Highlights](#Key-Highlights)
- [Key Objectives](#Key-Objectives)
- [Dataset Details](#Dataset-Details)
- [Tools & Technologies](#Tools-&Technologies)
- [Deliverables](#The-Deliverables)
- [Data Loading and Understanding](#Data-Loading-&Understanding)
- [Exploratory Data Analysis (EDA)](#Exploratory-Data-Analysis (EDA))
- [Data Analysis](#Data-Analysis)
- [Key Findings](#Key-Findings)
- [Recommendations](#The-Recommendations)
- [limitations](#The-limitations)
- [References](#The-References)

## Project Overview
---
The case study involves analyzing datasets provided by PhonePe to understand transaction trends, device usage patterns, and correlations with demographic data across states and districts. The project spans multiple years and quarters, providing a comprehensive view of user behavior and financial transactions in India.

### Key Highlights:
- Transaction Analysis: Analyzed trends in 5M+ transactions, identifying quarterly growth and payment behaviors.
- Device Insights: Explored 100K+ device records to uncover usage patterns of smartphones, feature phones, and other devices.
- Demographic Study: Assessed the impact of demographic factors on transactions, covering 700+ districts.
- Visualizations: Created 20+ charts and graphs to highlight trends and correlations.

### Key Objectives
- Analyzed transaction volumes and trends over time.
- Identified patterns in device usage for digital payments.
- Explored demographic correlations with transaction behavior.
- Ensured data consistency and derive advanced insights through statistical and visual analysis.

### Dataset Details
The dataset includes multiple sheets in an Excel file, each containing information on:

- Transaction data (volumes, values, and trends).
- Demographic data (state and district levels).
- Device usage statistics for PhonePe users.

### Tools & Technologies
- Python: For data manipulation and analysis.
- Pandas & NumPy: For data cleaning and transformation.
- Matplotlib & Seaborn: For data visualization.

### Deliverables
- Insights into transaction trends and patterns.
- Visualizations depicting transaction behavior and demographic relationships.
- A comprehensive analysis of device usage trends for digital payments.


### Data Loading and Understanding
In the initial phase,we performed the following tasks:
- Loading each dataset and displaying its structure
- Displaying basic statistics and data types for each dataset
- Checking for missing values
- Creating a Summary

### Exploratory Data Analysis (EDA)
- Analyzed transaction trends over the years for each state
- Identified the most common transaction types in each state and quarter
- Determined the Device Brand with the Highest Number of Registered Users in Each State


### Data Analysis
- There were some interesting Code/Features I have worked with:

#### 1. Handling Missing Values
Efficiently filled missing values in transaction data:

```python
# Handling missing values
df['transaction_amount'].fillna(method='ffill', inplace=True)
df['user_count'].fillna(method='bfill', inplace=True)
# Code written by Sidd!
```

#### 2. Outlier Detection and Removal
Implemented the IQR method to detect and eliminate outliers:

```python
# Detecting and removing outliers using IQR
Q1 = df['transaction_amount'].quantile(0.25)
Q3 = df['transaction_amount'].quantile(0.75)
IQR = Q3 - Q1
df_cleaned = df[(df['transaction_amount'] >= Q1 - 1.5 * IQR) & (df['transaction_amount'] <= Q3 + 1.5 * IQR)]
# Code written by Sidd!
```

#### 3. Visualizing Regional Trends
Generated insightful visualizations to compare transaction volumes across states:

```python
import matplotlib.pyplot as plt
import seaborn as sns

# Visualizing transaction trends across states
plt.figure(figsize=(12, 6))
sns.barplot(x='state', y='transaction_amount', data=df.groupby('state').sum().reset_index())
plt.xticks(rotation=90)
plt.title("State-wise Transaction Amounts")
plt.show()
# Code written by Sidd!
```

## Key Findings:
1. The total transaction amount has also increased, suggesting higher transaction values or more frequent transactions.
2. There is a positive correlation between population density and transaction volume, indicating that densely populated areas have higher transaction activity.
3. Total transactions have shown a consistent increase over time, indicating a growing adoption of digital transactions.

## Recommendations:
1. Focus marketing efforts on states and districts with high population density to maximize transaction volumes.
2. Develop targeted campaigns to further increase adoption in states showing rapid growth in transactions.
3. Monitor the growth trends regularly to identify any seasonal patterns or emerging markets.


## Limitations:
- Incomplete Data Coverage:
Some states and districts had missing transaction records, potentially skewing the analysis of regional trends.

- Correlation vs. Causation:
While demographic factors showed strong correlations with transaction trends, causation could not be definitively established.

## References:
- [stack_overflow](https://stackoverflow.com/)
- [PhonePe Dataset provided by Coding Ninjas.](https://classroom.codingninjas.com/app/classroom/me/25145/content/823859/offering/13998914)
