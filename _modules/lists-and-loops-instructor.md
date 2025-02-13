---
title: Lists and Loops Practice
---

# Working with Lists and Loops: A Historical Data Exercise

## Background

You explored lists and loops using the Bellevue Almshouse Dataset in Melanie Walsh's tutorials, which documented Irish immigrants in 1840s New York. Today we'll practice these concepts by analyzing some (fabricated) historical census data from the same time period.

## Setup

Launch Jupyter Lab and create a new notebook called `lists-loops-practice.ipynb`. Remember to:

- Add your last name to the start of the filename
- Save it in your `week-04` folder
- Use both Markdown and Code cells to document your work

## Getting Started with Census Data

Let's create some sample census data lists that we'll use throughout this tutorial:

```python
ages = [45, 23, 19, 34, 56, 28, 42, 31, 27, 38, 17, 52, 29, 44, 33, 25, 61, 36, 22, 41]

occupations = ['farmer', 'servant', 'laborer', 'merchant', 'farmer', 'servant', 'teacher', 'farmer', 'laborer', 'merchant', 'servant', 'farmer', 'laborer', 'blacksmith', 'carpenter', 'servant', 'farmer', 'weaver', 'servant', 'carpenter']

birth_places = ['Ireland', 'Ireland', 'New York', 'England', 'Ireland', 'Germany', 'New York', 'Ireland', 'Ireland', 'Scotland', 'Ireland', 'England', 'Ireland', 'Wales', 'Ireland', 'Ireland', 'Scotland', 'Ireland', 'Germany', 'Ireland']
```

## Exploring Our Lists

First, let's practice some basic list operations:

- Print the length of each list using `len()`
- Try slicing to show just the first 5 entries of the `occupations` list

```python
# Print lengths
print(f"Length of ages list: {len(ages)}")
print(f"Length of occupations list: {len(occupations)}")
print(f"Length of birth_places list: {len(birth_places)}")

# First 5 occupations using slicing
print("First 5 occupations:", occupations[:5])
```

## Building Lists with Loops

Let's identify all the farmers in our dataset:

```python
farmers = []
for occupation in occupations:
    if occupation == 'farmer':
        farmers.append(occupation)
```

### Practice Exercise

Create two new lists:

- One containing all individuals born in Ireland
- One containing all individuals under age 30

```python
# Find Irish-born individuals
irish_born = []
for i, birthplace in enumerate(birth_places):
    if birthplace == 'Ireland':
        irish_born.append(i)  # Storing index positions
print("Irish-born individuals found at positions:", irish_born)
print(f"Total Irish-born: {len(irish_born)} people")

# Find people under 30
young_people = []
for i, age in enumerate(ages):
    if age < 30:
        young_people.append(i)  # Storing index positions
print("People under 30 found at positions:", young_people)
print(f"Total under 30: {len(young_people)} people")
```

## Using Enumerate()

Let's add ID numbers to our records using the `enumerate()` function:

```python
for i, occupation in enumerate(occupations):
    print(f"Person #{i}: {occupation}")
```

### Practice Exercise

Use enumerate to print out each person's age and birthplace with an ID number

```python
# Print each person's info with ID number
for i, (age, birthplace) in enumerate(zip(ages, birth_places)):
    print(f"Person #{i}: Age {age}, born in {birthplace}")
```

## Working with Multiple Lists Using zip()

Let's combine information across our lists:

```python
for age, occupation, origin in zip(ages, occupations, birth_places):
    print(f"Age {age}, worked as {occupation}, born in {origin}")
```

### Practice Exercise

Use zip() to identify:

- All Irish-born farmers
- All merchants under 40

```python
# Find Irish-born farmers
print("Irish-born farmers:")
for age, occupation, origin in zip(ages, occupations, birth_places):
    if origin == 'Ireland' and occupation == 'farmer':
        print(f"Found Irish farmer: Age {age}")

# Find merchants under 40
print("\nMerchants under 40:")
for age, occupation, origin in zip(ages, occupations, birth_places):
    if occupation == 'merchant' and age < 40:
        print(f"Found young merchant: Age {age}, from {origin}")
```

## Analyzing Patterns with Counter

Import the Counter tool:

```python
from collections import Counter
```

Let's analyze:

- Most common occupations
- Most common birth places

```python
from collections import Counter

# Analyze occupations
occupation_counts = Counter(occupations)
print("Occupation distribution:")
for occupation, count in occupation_counts.most_common():
    print(f"{occupation}: {count}")

# Analyze birthplaces
birthplace_counts = Counter(birth_places)
print("\nBirth place distribution:")
for place, count in birthplace_counts.most_common():
    print(f"{place}: {count}")

# Calculate and print percentages for birthplaces
total_people = len(birth_places)
print("\nBirth place percentages:")
for place, count in birthplace_counts.most_common():
    percentage = (count / total_people) * 100
    print(f"{place}: {percentage:.1f}%")
```
