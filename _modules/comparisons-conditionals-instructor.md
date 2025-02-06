---
title: Comparisons and Conditionals (Instructor Copy)
---

# Working with Historical Census Data: Comparing Population Changes (Instructor Version)

## Setup

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

Check if Boston's population in 1870 was greater than 200,000:

```python
if boston_1870 > 200000:
    print(f"Boston's population in 1870 ({boston_1870}) was greater than 200,000")
else:
    print(f"Boston's population in 1870 ({boston_1870}) was less than 200,000")
```

Compare New York's and Philadelphia's populations in 1860:

```python
if ny_1860 > phil_1860:
    print(f"New York was larger with {ny_1860} people compared to Philadelphia's {phil_1860}")
else:
    print(f"Philadelphia was larger with {phil_1860} people compared to New York's {ny_1860}")
```

Check if Philadelphia's population doubled between 1850 and 1860:

```python
if phil_1860 >= (phil_1850 * 2):
    print("Philadelphia's population more than doubled between 1850 and 1860")
else:
    print("Philadelphia's population did not double between 1850 and 1860")
```

## Part 3: Population Growth Analysis

```python
# Calculate population growth
boston_growth = boston_1870 - boston_1850
ny_growth = ny_1870 - ny_1850
phil_growth = phil_1870 - phil_1850

# Compare growth rates
if boston_growth > ny_growth and boston_growth > phil_growth:
    print("Boston had the fastest growth!")
elif ny_growth > boston_growth and ny_growth > phil_growth:
    print("New York had the fastest growth!")
elif phil_growth > boston_growth and phil_growth > ny_growth:
    print("Philadelphia had the fastest growth!")
```

## Part 4: Complex Conditions

Check Boston's population conditions:

```python
if boston_1870 > 200000 and (boston_1870 - boston_1850) >= 100000:
    print("Boston met both population thresholds")
else:
    print("Boston did not meet both population thresholds")
```

Check New York or Philadelphia over 800,000:

```python
if ny_1860 > 800000 or phil_1860 > 800000:
    print("At least one city had over 800,000 people in 1860")
else:
    print("Neither city had over 800,000 people in 1860")
```

## Bonus Challenge Solution

```python
# Calculate percent growth
boston_pct_growth = ((boston_1870 - boston_1850) / boston_1850) * 100
ny_pct_growth = ((ny_1870 - ny_1850) / ny_1850) * 100
phil_pct_growth = ((phil_1870 - phil_1850) / phil_1850) * 100

# Categorize Boston's growth
if boston_pct_growth < 100:
    boston_category = "Low"
else:
    boston_category = "High"

# Categorize New York's growth
if ny_pct_growth < 100:
    ny_category = "Low"
else:
    ny_category = "High"

# Categorize Philadelphia's growth
if phil_pct_growth < 100:
    phil_category = "Low"
else:
    phil_category = "High"

print(f"Boston growth: {boston_category} ({boston_pct_growth:.1f}%)")
print(f"New York growth: {ny_category} ({ny_pct_growth:.1f}%)")
print(f"Philadelphia growth: {phil_category} ({phil_pct_growth:.1f}%)")
```
