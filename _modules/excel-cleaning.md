---
title: Working With and Cleaning Excel Files
---

## Introduction

Excel files often contain messy, inconsistent data spread across multiple sheets. This tutorial will guide you through common data cleaning tasks using Python's pandas library.

## Loading the Excel File

**Problem**: We need to access all sheets in our Excel workbook.
**Solution**: Use pandas' `read_excel()` function with `sheet_name=None` to load all sheets into a dictionary.

### Examining the Sheets and Their Data

**Problem**: We need to understand what data is in each sheet.
**Solution**: Create a loop to display the names of all sheets and preview each sheet's data.

### Correcting Data Types

**Problem**: Excel sometimes imports numeric data as strings or objects.
**Solution**: Use `df.dtypes` to check column types, then `pd.to_numeric()` to convert columns to appropriate numeric types.

### 5. Handling Inconsistent Text Data

**Problem**: Text data may contain inconsistent capitalization, extra spaces, etc.
**Solution**: Use string methods like `.str.strip()`, `.str.lower()`, or `.str.replace()` to clean text fields.

### 6. Removing Duplicate Records

**Problem**: Datasets might contain duplicate entries.
**Solution**: Use `df.duplicated()` to identify duplicates and `df.drop_duplicates()` to remove them.

### 7. Filtering and Sorting Data

**Problem**: We may need to focus on specific subsets of the data.
**Solution**: Use boolean indexing for filtering and `df.sort_values()` for sorting.

### 8. Merging Data from Multiple Sheets

**Problem**: Related data might be split across different sheets.
**Solution**: Use `pd.merge()` or `pd.concat()` to combine data from different sheets.

### 9. Handling Date and Time Data

**Problem**: Date formats in Excel can be inconsistent.
**Solution**: Use `pd.to_datetime()` to convert columns to datetime format.

### 10. Creating Summary Statistics

**Problem**: We need insights from our cleaned data.
**Solution**: Use methods like `df.describe()`, `df.groupby()`, or `df.pivot_table()` to summarize data.

### 11. Exporting Clean Data

**Problem**: After cleaning, we need to save our work.
**Solution**: Use `df.to_excel()` or `df.to_csv()` to export the cleaned dataset.

# Cleaning Messy Excel Data

## Setup and Installation

First, let's import the necessary libraries:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

## 1. Loading the Excel File

We'll load all sheets from our Excel file into a dictionary:

```python
# Load all sheets into a dictionary
excel_file = 'university_data.xlsx'
all_sheets = pd.read_excel(excel_file, sheet_name=None)

# Print the names of all sheets
print("Sheets in the workbook:")
for sheet_name in all_sheets.keys():
    print(f"- {sheet_name}")
```

## 2. Examining the Sheets and Their Data

Let's look at each sheet to understand the data:

```python
# Loop through each sheet and display basic info
for sheet_name, df in all_sheets.items():
    print(f"\n\nSheet: {sheet_name}")
    print(f"Shape: {df.shape}")
    print("\nFirst 5 rows:")
    print(df.head())
    print("\nColumn names:")
    print(df.columns.tolist())
    print("\nData types:")
    print(df.dtypes)
```

## 4. Correcting Data Types

Let's check and fix data types:

```python
# Check data types
print("Current data types:")
print(df.dtypes)

# Example: Convert a column that should be numeric
# Assume 'column_name' should be numeric
# df['column_name'] = pd.to_numeric(df['column_name'], errors='coerce')

# After conversion, check again
# print("\nData types after conversion:")
# print(df.dtypes)
```

## 5. Handling Inconsistent Text Data

Let's clean up text data:

```python
# Example: Clean up a text column
# Assume 'text_column' needs cleaning
# df['text_column'] = df['text_column'].str.strip().str.lower()

# Example: Replace specific text
# df['text_column'] = df['text_column'].str.replace(' ', '_')

# Display the cleaned column
# print(df['text_column'].head())
```

## 6. Removing Duplicate Records

Identify and remove any duplicate records:

```python
# Check for duplicates
print(f"Number of duplicate rows: {df.duplicated().sum()}")

# Remove duplicates
df_no_dupes = df.drop_duplicates()
print(f"Shape after removing duplicates: {df_no_dupes.shape}")
```

## 7. Filtering and Sorting Data

Filter and sort the data:

```python
# Example: Filter rows where a column meets a condition
# filtered_df = df[df['column_name'] > 50]
# print(f"Shape after filtering: {filtered_df.shape}")

# Example: Sort by a column
# sorted_df = df.sort_values('column_name', ascending=False)
# print("Top 5 rows after sorting:")
# print(sorted_df.head())
```

## 8. Merging Data from Multiple Sheets

Combine data from different sheets:

```python
# Example: Merge two dataframes (sheets) on a common column
# Assuming two sheets have a common column 'id':
# sheet1 = all_sheets['Sheet1']
# sheet2 = all_sheets['Sheet2']
# merged_df = pd.merge(sheet1, sheet2, on='id', how='inner')
# print(f"Shape of merged dataframe: {merged_df.shape}")
```

## 9. Handling Date and Time Data

Process date/time columns:

```python
# Example: Convert a column to datetime
# df['date_column'] = pd.to_datetime(df['date_column'], errors='coerce')
# print(df['date_column'].head())

# Example: Extract components from datetime
# df['year'] = df['date_column'].dt.year
# df['month'] = df['date_column'].dt.month
# print(df[['date_column', 'year', 'month']].head())
```

## 10. Creating Summary Statistics

Generate insights from the data:

```python
# Basic statistics
print("Summary statistics:")
print(df.describe())

# Example: Group by a category and calculate means
# grouped = df.groupby('category_column').mean()
# print(grouped)

# Example: Pivot table
# pivot = df.pivot_table(
#    values='value_column',
#    index='row_category',
#    columns='column_category',
#    aggfunc='mean'
# )
# print(pivot)
```

## 11. Exporting Clean Data

Save the cleaned data:

```python
# Export to Excel
# df.to_excel('cleaned_data.xlsx', index=False)

# Export to CSV
# df.to_csv('cleaned_data.csv', index=False)

print("Data cleaning complete!")
```
