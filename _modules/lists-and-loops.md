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

## Using Enumerate()

Let's add ID numbers to our records using the `enumerate()` function:

```python
for i, occupation in enumerate(occupations):
    print(f"Person #{i}: {occupation}")
```

### Practice Exercise

Use enumerate to print out each person's age and birthplace with an ID number

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

## Analyzing Patterns with Counter

Import the Counter tool:

```python
from collections import Counter
```

Let's analyze:

- Most common occupations
- Most common birth places
