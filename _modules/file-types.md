---
title: Working With Different File Types
---

## Introduction

In real-world data analysis, you'll rarely encounter perfectly formatted CSV files. Data often comes in various formats and requires cleaning before it can be properly analyzed. This tutorial will help you learn:

- How to read data from different file formats
- How to handle common file format challenges
- Basic techniques for cleaning string data

## Part 1: File Types Overview

Common data file formats you'll encounter:

- **CSV (Comma-Separated Values)**
  - Most common data format
  - Each value separated by commas (`,`)
  - Example: `name,age,city`
- **TXT (Text files with different delimiters)**
  - Similar to CSV but may use different "separators" instead of commas (`,`)
  - Common separators include: tabs (`\t`), pipes (`|`), or semicolons (`;`)
  - Example: `name|age|city`
- **Excel files (XLS/XLSX)**
  - Spreadsheet format
  - Can contain multiple sheets
  - Support more complex, visual formatting but can be harder to work with in Python

## Part 2: Reading Different File Types with Pandas

### Reading Tab-Delimited Files

Tab-delimited files are like CSV files but use tabs instead of commas as separators.

```python
# Read a tab-delimited file
df = pd.read_csv("historical_figures.txt", sep="\t")
```

### Reading Excel Files

Excel files can be read with the `read_excel()` function:

```python
# Basic reading (first sheet)
df = pd.read_excel("university_data.xlsx")

# See available sheets
excel_file = pd.ExcelFile("university_data.xlsx")
print(excel_file.sheet_names)

# Read a specific sheet
df = pd.read_excel("university_data.xlsx", sheet_name="Sheet2")

# Read all sheets into a dictionary of DataFrames
all_dfs = pd.read_excel("university_data.xlsx", sheet_name=None)
```

### Handling Encoding Issues

If you encounter strange characters when reading a file, you might need to specify the encoding:

```python
# Common encodings: utf-8, latin-1, cp1252
df = pd.read_csv("file.txt", sep="\t", encoding="utf-8")
```

## Part 3: Basic String Cleaning Techniques

### Cleaning Column Names

```python
# Convert column names to lowercase and replace spaces with underscores
df.columns = [col.lower().replace(' ', '_') for col in df.columns]

# Strip whitespace from column names
df.columns = [col.strip() for col in df.columns]

# Rename specific columns
df = df.rename(columns={'old_name': 'new_name', 'another_old': 'another_new'})
```

### Cleaning String Data

```python
# Remove leading/trailing whitespace
df['column'] = df['column'].str.strip()

# Convert to lowercase
df['column'] = df['column'].str.lower()

# Convert to uppercase
df['column'] = df['column'].str.upper()

# Capitalize first letter
df['column'] = df['column'].str.capitalize()

# Title case (capitalize first letter of each word)
df['column'] = df['column'].str.title()
```

## Hands-On Exercise

In this exercise, you'll work with two files:

1. `historical_figures.txt` - A tab-delimited file containing information about computing pioneers
2. `university_data.xlsx` - An Excel file with multiple sheets about university statistics

Your tasks:

- Load both files correctly
- Clean up at least one string column in each file
- Rename columns to be more descriptive

### Getting Started

First, load the tab-delimited file:

```python
historical_df = pd.read_csv("historical_figures.txt", sep="\t")
historical_df.head()
```

Then load the Excel file:

```python
# You can choose which sheet to work with
enrollment_df = pd.read_excel("university_data.xlsx", sheet_name="Enrollment")
enrollment_df.head()
```
