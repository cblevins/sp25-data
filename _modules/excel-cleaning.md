---
title: Cleaning Excel Files
---

This tutorial will go through opening an Excel file and some common ways you might need to clean data.

## Initial Data Examination

This initial step is crucial because it gives you your first look at the data structure. You need to understand how many rows and columns you're working with as a starting point. The `shape` attribute tells you exactly that, while the `head()` method shows you the first few rows so you can see actual values and get a feel for what kind of data you're dealing with. This helps you identify obvious issues immediately and plan your cleaning approach.

### Load the data and explore basic information

```python
import pandas as pd

# Load both sheets
enrollment_df = pd.read_excel('university_data.xlsx', sheet_name='Enrollment')
tuition_df = pd.read_excel('university_data.xlsx', sheet_name='Tuition')

# View basic information
print(enrollment_df.shape)  # Check number of rows and columns
print(tuition_df.shape)

# Preview the data
print(enrollment_df.head())
print(tuition_df.head())
```

### Check column names and data types

Understanding column names and data types is essential because inconsistent naming conventions can cause problems when merging datasets later. You want to ensure numerical columns are actually stored as numbers (not strings), which affects calculations you might need to perform. Incorrect data types can lead to unexpected behavior in your analysis - for example, if enrollment numbers were stored as strings, you couldn't calculate averages correctly.

```python
# Examine column names
print(enrollment_df.columns)
print(tuition_df.columns)

# Check data types
print(enrollment_df.dtypes)
print(tuition_df.dtypes)
```

### Check for duplicates

Duplicate entries can significantly skew your analysis results. For instance, if Harvard appears twice in the dataset with the same values, any aggregations like averages or sums would be incorrectly weighted. You need to identify these duplicates to decide whether they're actual errors that need to be removed or legitimate repeats.

```python
# Check for duplicate rows in the enrollment dataframe
print(enrollment_df.duplicated())
print("Duplicate rows in enrollment data:")
print(enrollment_df[enrollment_df.duplicated()])


# Check for duplicate rows in the tuition dataframe
print(tuition_df.duplicated())
print("Duplicate rows in tuition data:")
print(tuition_df[tuition_df.duplicated()])
```

### Check for unique values across all columns

Examining unique values helps you identify inconsistencies within each column. For university names, you might find variations like "Harvard," "harvard university," and "Harvard University" that all refer to the same institution. For numerical columns, unusual values might indicate outliers or data entry errors. This step is particularly important for categorical data where consistency is key for proper grouping and analysis.

```python
# Check unique values in all columns
for column in enrollment_df.columns:
    print(f"Column: {column}")
    print(enrollment_df[column].unique())
    print("---")

for column in tuition_df.columns:
    print(f"Column: {column}")
    print(tuition_df[column].unique())
    print("---")
```

## Identifying Common Data Issues

Based on analysis, these are likely issues that need cleaning:

**Inconsistent university naming**:

- Case inconsistencies (lowercase vs. title case)
- Extra whitespace in university names
- Same universities might be written differently between sheets

**Inconsistent column naming**:

- "University" vs "university" (capitalization differences)
- Extra spaces in column names (e.g., `International  students`)
- Inconsistent formatting ("Average_financial_aid")

**Duplicate records**:

- The Enrollment sheet has duplicate rows

## Data Cleaning Steps using Pandas

Cleaning column names is a fundamental preprocessing step because inconsistent naming makes your code more error-prone and harder to read. By standardizing names (making everything lowercase, replacing spaces with underscores), you create a consistent naming pattern that's easier to work with in code. This is especially important when you have to reference columns repeatedly in your analysis. Additionally, standardizing names between dataframes ensures that when you merge them later, the columns will align properly.

```python
# Strip whitespace, standardize case, replace multiple spaces in column names
enrollment_df.columns = [col.strip().lower().replace('   ', '_').replace(' ', '_') for col in enrollment_df.columns]
tuition_df.columns = [col.strip().lower().replace('_', '').replace(' ', '_') for col in tuition_df.columns]

print(enrollment_df.columns)
print(tuition_df.columns)
```

The `university` column is our main identifier for the dataset, so cleaning them is critical. Inconsistent capitalization (Harvard vs. harvard) and extra whitespace ("MIT " vs "MIT") would prevent proper matching when merging data. By standardizing case and removing whitespace, you ensure that "Harvard University" and "harvard university " will be treated as the same entity. This step is crucial for data integrity and allows for accurate analysis across multiple datasets.

```python
# Strip whitespace and standardize case for univeresity names
enrollment_df['university'] = enrollment_df['university'].str.strip().str.title()
tuition_df['university'] = tuition_df['university'].str.strip().str.title()

# note what happens to UC Berkeley with the title() function...

print(enrollment_df['university'])
print(tuition_df['university'])
```

Finally, looking for duplicate values ensures that each university appears only once in your dataset. Duplicate entries can significantly distort your analysis - for example, if Harvard appears twice with the same enrollment numbers, your total student count would be inflated. In educational data analysis, each institution should typically have one record per time period. The drop_duplicates() method efficiently removes these redundant entries, resulting in a cleaner dataset that will produce more accurate statistics.

```python
# Remove duplicate rows based on a column
enrollment_df = enrollment_df.drop_duplicates(subset=['university'])
```

## Merging the Two Sheets

Merging datasets brings together related information from different sources into a single, comprehensive dataset. Here, we're combining enrollment and tuition information to enable more complex analyses. We use an outer join to include all universities from both sheets, even if they only appear in one sheet. This approach prevents data loss and maintains the integrity of your dataset.

```python
# Merge the enrollment and tuition data on the cleaned university name
merged_df = pd.merge(
    enrollment_df,
    tuition_df,
    on='university',
    how='outer'  # Use outer join to keep all universities from both sheets
)
```

Saving to CSV format creates portable, universally readable files that can be easily shared or imported into other analysis tools. The index=False parameter prevents adding unnecessary row indices to your output files.

```python
# Save the data to CSV file
merged_df.to_csv('university_data_merged.csv', index=False)
```
