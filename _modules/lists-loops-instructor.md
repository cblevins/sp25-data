---
title: Lists and Loops Practice Instructor Version
---

# Working with Lists and Loops: A Historical Data Exercise [INSTRUCTOR ANSWER KEY]

## Background

[Same as student version]

## Setup

[Same as student version]

## Getting Started with Census Data

Initial data setup code remains the same:

```python
ages = [45, 23, 16, 34, 64, 28, 42, 31, 27, 38, 17, 52, 29, 44, 33, 15, 61, 36, 18, 41]

occupations = ['farmer', 'servant', 'laborer', 'merchant', 'farmer', 'servant', 'teacher', 'farmer', 'laborer', 'merchant', 'servant', 'farmer', 'laborer', 'blacksmith', 'carpenter', 'servant', 'farmer', 'weaver', 'servant', 'carpenter']

birth_places = ['Ireland', 'Ireland', 'New York', 'England', 'Ireland', 'Germany', 'New York', 'Ireland', 'Ireland', 'Scotland', 'Ireland', 'England', 'Ireland', 'Wales', 'Ireland', 'Ireland', 'Scotland', 'Ireland', 'Germany', 'Ireland']
```

## Exploring Our Lists

Solution for basic list operations:

```python
# Print lengths
print(f"Length of ages list: {len(ages)}")
print(f"Length of occupations list: {len(occupations)}")
print(f"Length of birth_places list: {len(birth_places)}")

# First 5 occupations
print(occupations[:5])
```

Expected output:

```
Length of ages list: 20
Length of occupations list: 20
Length of birth_places list: 20
['farmer', 'servant', 'laborer', 'merchant', 'farmer']
```

## Analyzing Patterns with Counter

Initial Counter example remains the same:

```python
from collections import Counter
print(Counter(occupations))
```

Expected output:

```
Counter({'farmer': 6, 'servant': 6, 'laborer': 3, 'merchant': 2, 'carpenter': 2, 'teacher': 1, 'blacksmith': 1, 'weaver': 1})
```

### Practice Exercise Solution

```python
# Most common birth places
print(Counter(birth_places))
```

Expected output:

```
Counter({'Ireland': 11, 'England': 2, 'New York': 2, 'Germany': 2, 'Scotland': 2, 'Wales': 1})
```

## Using Enumerate()

### Practice Exercise Solution

```python
for number, (age, birthplace) in enumerate(zip(ages, birth_places)):
    print(f"Person #{number}: Age {age}, born in {birthplace}")
```

Expected output:

```
Person #0: Age 45, born in Ireland
Person #1: Age 23, born in Ireland
[...]
```

## Building Lists with Loops Part 1

### Practice Exercise Solution

```python
# UK-born individuals
uk_born = []
for birthplace in birth_places:
    if birthplace in ['Ireland', 'England', 'Wales', 'Scotland']:
        uk_born.append(birthplace)
print(f"Number of UK-born individuals: {len(uk_born)}")
print(f"UK-born individuals: {uk_born}")

# Under 30
under_30 = []
for age in ages:
    if age < 30:
        under_30.append(age)
print(f"Number of people under 30: {len(under_30)}")
print(f"Ages under 30: {under_30}")
```

Expected output:

```
Number of UK-born individuals: 16
UK-born individuals: ['Ireland', 'Ireland', 'England', 'Ireland', 'Ireland', 'Ireland', 'Scotland', 'Ireland', 'England', 'Ireland', 'Wales', 'Ireland', 'Ireland', 'Scotland', 'Ireland', 'Ireland']
Number of people under 30: 7
Ages under 30: [23, 16, 28, 27, 17, 29, 15, 18]
```

## Building Lists with Loops Part 2

### Practice Exercise Solution

```python
age_group = []
for age in ages:
    if age < 18:
        age_group.append("youth")
    elif age <= 50:
        age_group.append("adult")
    else:
        age_group.append("elderly")

print(Counter(age_group))
```

Expected output:

```
Counter({'adult': 15, 'elderly': 3, 'youth': 2})
```

## Working with Multiple Lists Using zip()

### Practice Exercise Solution

```python
# Find Irish-born farmers
print("Irish-born farmers:")
for age, occupation, origin in zip(ages, occupations, birth_places):
    if origin == 'Ireland' and occupation == 'farmer':
        print(f"Age {age}, worked as {occupation}, born in {origin}")

# Find merchants under 40
print("\nMerchants under 40:")
for age, occupation, origin in zip(ages, occupations, birth_places):
    if occupation == 'merchant' and age < 40:
        print(f"Age {age}, worked as {occupation}, born in {origin}")
```

Expected output:

```
Irish-born farmers:
Age 45, worked as farmer, born in Ireland
Age 28, worked as farmer, born in Ireland
Age 31, worked as farmer, born in Ireland
Age 52, worked as farmer, born in Ireland
Age 61, worked as farmer, born in Ireland

Merchants under 40:
Age 34, worked as merchant, born in England
Age 38, worked as merchant, born in Scotland
```
