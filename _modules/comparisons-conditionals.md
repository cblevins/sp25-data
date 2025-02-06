---
title: Comparisons and Conditionals
---

This in-class exercise will help you practice using Python comparisons and conditionals while exploring some historical census data from 19th century American cities.

## Setup

- Create a new Jupyter notebook in your `week-03` folder named `lastname-comparisons-conditionals.ipynb`
- We'll use variables to store population data for different cities and years
- Remember to use descriptive variable names and add comments to explain your code

## Part 1: Creating Variables

First, let's create some variables with historical census data. Copy and paste this code into a new code cell:

```python
# Boston population data
boston_1850 = 136881
boston_1860 = 177840
boston_1870 = 250526

# New York population data
ny_1850 = 515547
ny_1860 = 813669
ny_1870 = 942292

# Philadelphia population data
phil_1850 = 121376
phil_1860 = 565529
phil_1870 = 674022
```

## Part 2: Basic Comparisons

Use comparison operators and `if/else statements` to answer these questions about the cities:

- Write code to check if Boston's population in 1870 had surpassed `200,000` people
- Compare New York's and Philadelphia's populations in 1860 using an `if/else statement` - which was larger?
- Did Philadelphia's population **more than double** between 1850 and 1860?

## Part 3: Population Growth Analysis

Now let's analyze population growth across each of the cities between 1850 and 1870. To get started, copy the following into a new code cell to establish how much each city grew by in each year:

```python
# Calculate population growth
boston_growth = boston_1870 - boston_1850
ny_growth = ny_1870 - ny_1850
phil_growth = phil_1870 - phil_1850
```

- Write an `if/elif/else statement` that prints "Fastest growing city!" if a city had the **highest absolute population growth** (ie. went up by the largest number of people).

## Part 4: Complex Conditions

Let's combine multiple conditions:

- Write code using `and` to check if **BOTH**:
  - Boston's 1870 population was over 200,000
  - **AND** Boston's population increased by at least 100,000 from 1850 to 1870
- Use `or` to check if either one of these condition was true in 1860:
  - New York's population was over 800,000 in 1860
  - **OR** Philadelphia's population was over 800,000 in 1860

## Bonus Challenge

- Create variables for the **percent growth** (rather than absolute growth) of each city between 1850-1870 - ex. "Philadelphia grew xx% between 1850 and 1870
- Use `if/else statements` to categorize each city as "Low Growth" if it grew by LESS than 100% and "High Growth" if it grew by MORE than 100%
