---
title: Lists and Loops Practice
---

# Working with Lists and Loops: A Historical Data Exercise

## Background

You explored lists and loops using the Bellevue Almshouse Dataset in Melanie Walsh's tutorials, which documented Irish immigrants in 1840s New York. Today we'll practice these concepts by analyzing some (fabricated) historical census data from the same time period.

## Setup

Launch Jupyter Lab and create a new notebook called `lists-loops-practice.ipynb`. Remember to:

- Add your last name to the start of the filename
- Save it in a `week-04` folder
- Use both Markdown and Code cells to document your work

## Getting Started with Census Data

Let's create some sample census data lists that we'll use throughout this tutorial. Copy and paste this into a new code cell in your notebook:

```python
ages = [45, 23, 16, 34, 64, 28, 42, 31, 27, 38, 17, 52, 29, 44, 33, 15, 61, 36, 18, 41]

occupations = ['farmer', 'servant', 'laborer', 'merchant', 'farmer', 'servant', 'teacher', 'farmer', 'laborer', 'merchant', 'servant', 'farmer', 'laborer', 'blacksmith', 'carpenter', 'servant', 'farmer', 'weaver', 'servant', 'carpenter']

birth_places = ['Ireland', 'Ireland', 'New York', 'England', 'Ireland', 'Germany', 'New York', 'Ireland', 'Ireland', 'Scotland', 'Ireland', 'England', 'Ireland', 'Wales', 'Ireland', 'Ireland', 'Scotland', 'Ireland', 'Germany', 'Ireland']
```

## Exploring Our Lists

Each of these lists have 20 items, with each item corresponding to the attribute of a different individual person. For instance, the first item in each list has attributes about the same individual:

- 45 years old
- Works as a farmer
- Born in Ireland

### Practice Exercise

Let's practice some basic list operations:

- Print the length of each list using `len()`
- Try slicing to show just the first 5 entries of the `occupations` list

## Analyzing Patterns with Counter

Let's use the Counter tool to take a quick look at the most common values for some of our lists. Let's start with `occupations`:

```python
from collections import Counter
Counter(occupations)
```

### Practice Exercise

Use the Counter() tool to analyze:

- The most common birth places

## Using Enumerate()

Let's attach some ID numbers to our individuals using the `enumerate()` function. Remember, you can

```python
for number, occupation in enumerate(occupations):
    print(f"Person #{number}: {occupation}")
```

### Practice Exercise

Use enumerate() to print out each person's **age** and **birthplace** along with an **ID number**

## Building Lists with Loops Part 1

Let's create a new list that just contains what people at this time period would call "skilled laborers": a `blacksmith`, `carpenter` or `weaver`. Then print that list along with how many people fall into this category.

```python
skilled_laborers = []
for occupation in occupations:
    if occupation == 'blacksmith' or occupation == 'carpenter' or occupation == 'weaver':
        skilled_laborers.append(occupation)
print(f"Number of skilled laborers: {len(skilled_laborers)}")
```

### Practice Exercise

Create two new lists:

- One containing all individuals born in the **United Kingdom** (ie. in either `Ireland` or `England` or `Wales`)
- One containing all individuals **under the age of 30**

## Building Lists with Loops Part 2

Let's say we wanted to create a new list that wasn't just ONLY the "skilled laborers". Instead, we want a new list that designates whether or not each of the 20 people are the following: `skilled laborer`, `unskilled laborer`, or `other`. Then let's use Counter() to get a sense for how many people fall into each of these larger categories.

```python
skilled_unskilled = []
for occupation in occupations:
    if occupation == 'blacksmith' or occupation == 'carpenter' or occupation == 'weaver':
        skilled_unskilled.append("skilled laborer")
    elif occupation == 'laborer' or occupation == 'servant' or occupation == 'farmer':
        skilled_unskilled.append("unskilled laborer")
    else:
        skilled_unskilled.append("other")
Counter(skilled_unskilled)
```

### Practice Exercise

Create a new list named `age_group`

- This list should have three categories in it: `youth` (under 18), `adult` (18-50), and `elderly` (over 50)

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
