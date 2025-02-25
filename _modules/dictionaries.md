---
title: Dictionaries Practice
---

## Overview

Last week, you practiced using lists and loops with historical census data. Today, we're going to practice using dictionaries alongside lists and loops.

## Setup

Launch Jupyter Lab and create a new notebook called `yourlastname-dictionaries-practice.ipynb`. Remember to:

- Add your last name to the start of the filename (e.g., `blevins-dictionaries-practice.ipynb`)
- Save it in a `week-06` folder
- Use both Markdown and Code cells to document your work

## Lists vs. Dictionaries

You've now learned about two different data structures: lists and dictionaries. There are some parallels between the two but it's important to understand their differences.

Lists:

- Are **ordered** collections - ie. the particular sequence or order matters
- Best for sequential data
- Accessed using square brackets with an index number: `my_list[3]`
- Can have duplicate items

Dictionaries:

- Are **unordered** collections - ie. the particular sequence or order doesn't matter
- Best for labeled data where you want to look up a specific item
- Accessed using square brackets with a key: `my_dict["key"]`
- Cannot have duplicate items

Here's how the differences look in Python:

```python
# A list of names
names_list=["Patrick Murphy", "Mary Kelly", "Thomas Williams", "Elizabeth Smith"]

# A list of ages
ages_list = [45, 23, 16, 34, 64]

# A dictionary of names and ages
ages_dict = {
    "Patrick Murphy": 45,
    "Mary Kelly": 23,
    "Thomas Williams": 16,
    "Elizabeth Smith": 34,
}
```

With a list, the only way to access particular items is by knowing their position within the list's sequential order of items. So we could access the second item in the list of ages: with `ages_list[1]`, which would return `23`.

With a dictionary, we can get someone's age by looking up their name in the dictionary - and we don't need to know whether this is the second entry, the fifth entry, the 100th entry, etc. All we need is the `value`. In this case, their name: `ages_dict["Mary Kelly"]` would also return `23`.

### When to Use Each

- Use lists when order matters and you want to access items by position
- Use dictionaries when you want to access items by a meaningful and unique label or name
- Lists are great for loops - iterating through all items in sequence
- Dictionaries are excellent for looking up specific values by their identifier (provided those identifiers are unique)

## Creating Your First Dictionary

Let's start with the simplest case - creating a dictionary that maps people's names to their ages. Copy and paste the following into a code cell and run the cell:

```python
# Create a dictionary mapping names to ages
ages_dict = {
    "Patrick Murphy": 45,
    "Mary Kelly": 23,
    "Thomas Williams": 16,
    "Elizabeth Smith": 34
}

# Print the entire dictionary
print(ages_dict)
```

### Accessing Dictionary Values

Unlike lists which use numerical positions (indices), dictionaries use keys to access values:

```python
# Get Patrick's age using his name as the key
patricks_age = ages_dict["Patrick Murphy"]
print(f"Patrick Murphy is {patricks_age} years old.")
```

### Practice: Creating a Dictionary

Below is a list of some famous celebrities and their ages (as of 2025):

- Taylor Swift, 35
- Olivia Rodrigo, 22
- Tom Hanks, 68
- Meryl Streep, 75

Create a dictionary called `celebrity_ages` that uses each celebrity's name as a `key` and their age as the `value`. Then:

- Print the entire dictionary
- Print Zendaya's age

## Adding and Modifying Dictionary Entries

Let's go back to our fictionalized census dictionary. Dictionaries are "mutable," meaning we can add new key-value pairs or change existing ones.

Here's how we would add a new person and their age (a `key-value pair`) to our dictionary:

```python
# Add a new person to our ages dictionary
ages_dict["Michael Sullivan"] = 64
print(ages_dict)
```

We can also modify existing entries in our dictionary. Let's say Thomas just had a birthday and we need to update his age. We would access this entry in the dictionary by calling his `key` square brackets `[]` and then overwrite whatever `value` is associated with that key.

```python
# Change someone's age
ages_dict["Thomas Williams"] = 17  # Thomas just had a birthday!
print(f"Updated age for Thomas: {ages_dict['Thomas Williams']}")
```

### Practice: Modifying Your Dictionary

- Add one new entry to your celebrity dictionary of any celebrity you want with their age
- Change the age of one celebrity from your dictionary
- Print the updated dictionary

## Combining Dictionaries and Loops

We can iterate through a dictionary using loops in two different ways.

```python
# Loop through all names and ages
for name in ages_dict:
    print(f"{name} is {ages_dict[name]} years old.")

# A more elegant way using the .items() method
for name, age in ages_dict.items():
    print(f"{name} is {age} years old.")
```

We can also combine conditionals with loops. Let's loop through our dictionary and only print the names and ages of people who are over 30 years old:

```python
# Find all people over 30
for name, age in ages_dict.items():
    if age > 30:
        print(f"{name} is {age} years old.")
```

### Practice: Printing Age Cohorts

Use the `.items()` method to loop through your dictionary of celebrities. Use a series of `if` and `elif` conditionals to print out, for each celebrity, which age cohort they fall in:

- Gen Z: 13-28
- Millenial: 29-44
- Boomer: 61-79

## Creating a Nested Dictionary

Now let's suppose we wanted a more complex dictionary of people that included more information about an individual beyond just their age. To do that we can use a nested dictionary structure. Each `key` (item) in the main dictionary is a single person's name. Then the `value` for that item is _itself_ a dictionary with additional information.

```python
# Create one dictionary with all information about each person
census_data = {
    "Patrick Murphy": {
        "age": 45,
        "birth_place": "Ireland",
        "occupation": "farmer"
    },
    "Mary Kelly": {
        "age": 23,
        "birth_place": "Ireland",
        "occupation": "servant"
    },
    "Thomas Williams": {
        "age": 17,
        "birth_place": "Wales",
        "occupation": "laborer"
    },
    "Elizabeth Smith": {
    "age": 34,
    "birth_place": "England",
    "occupation": "servant"
    }
}
```

We could then access individual entries or drill down to get specific information.

```python
# Access data from our nested dictionary
print(census_data["Patrick Murphy"])
print(census_data["Patrick Murphy"]["occupation"])
```

### Practice Accessing Nested Dictionaries

Write a print statement that prints out Mary Kelly's age.

## Creating a Nested Dictionary with Loops

Typing out all this information manually is tedious. Now imagine if our dictionary was 4,000 entries instead of just 4! We can use our knowledge of lists and loops to automatically create this dictionary based on existing data. Let's imagine we have several lists of information about the same set of people. Copy and paste the following code into a new code cell:

```python
# Here are our lists of data
names = ["Patrick Murphy", "Mary Kelly", "Thomas Williams", "Elizabeth Smith", "Michael Sullivan",
         "Anna Schmidt", "William Johnson", "James O'Connor", "Bridget Walsh", "Robert Campbell",
         "Catherine Miller", "George Thompson", "Sean O'Neill", "David Jones", "Kevin Burke",
         "Margaret Wilson", "Donald Fraser", "Eileen Doyle", "Frieda Weber", "Timothy Ryan"]

ages = [45, 23, 16, 34, 64, 28, 42, 31, 27, 38, 17, 52, 29, 44, 33, 15, 61, 36, 18, 41]

birth_places = ['Ireland', 'Ireland', 'New York', 'England', 'Ireland', 'Germany', 'New York',
               'Ireland', 'Ireland', 'Scotland', 'Ireland', 'England', 'Ireland', 'Wales',
               'Ireland', 'Ireland', 'Scotland', 'Ireland', 'Germany', 'Ireland']

occupations = ['farmer', 'servant', 'laborer', 'merchant', 'farmer', 'servant', 'teacher', 'farmer',
              'laborer', 'merchant', 'servant', 'farmer', 'laborer', 'blacksmith', 'carpenter',
              'servant', 'farmer', 'weaver', 'servant', 'carpenter']
```

Our goal is to use a `for` statement to go through these lists, access the same position in each of them, and stitch all this information into a single dictionary. Conceptually, it looks something like this:

- Create an empty dictionary called `auto_census`
- Start a loop that goes through each position (index) in our lists (running sequentially from 0 to 19)

* For each position:
  - Get the `name` at that position and add it to a temporary variable
  - Get the `age` at that position and add it to a temporary variable
  - Get the `birth_place` at that position and add it to a temporary variable
  - Get the `occupation` at that position and add it to a temporary variable
* Add a new entry to our dictionary:
  - Use the person's name as the main key
  - Create a nested dictionary as the value that contains information about their age, birth place, and occupation

```python
# Start with an empty dictionary
auto_census = {}

# Loop through the lists to create our nested dictionary
for i in range(len(names)):
    # Extract the data for this person and temporarily put the data into a series of variables
    name = names[i]
    age = ages[i]
    birth_place = birth_places[i]
    occupation = occupations[i]

    # Create the nested dictionary for this person
    auto_census[name] = {
        "age": age,
        "birth_place": birth_place,
        "occupation": occupation
    }
```

Let's check and see what we made:

```python
#Print out the entry for Anna Schmidt
print(auto_census["Anna Schmidt"])

#Print out the birth place of Donald Fraser
print(auto_census["Donald Fraser"]["birth_place"])
```

### Practice Creating a Nested Dictionary With Loops

Your task:

- Create an empty dictionary called `celebrity_info`
- Use a loop to populate this dictionary with nested dictionaries for each celebrity - each nested dictionary should contain their age, birth place, and occupation
- Once you've created your dictionary, use a loop to find and print each celebrity who is an actor

Here is the starting data you can copy and paste to get started:

```python
# Celebrity information
names = ["Taylor Swift", "Olivia Rodrigo", "Tom Hanks", "Meryl Streep"]
ages = [35, 22, 68, 75]
birth_places = ["Pennsylvania", "California", "California", "New Jersey"]
occupations = ["singer", "singer", "actor", "actor"]
```

## Bonus Activities

### Bonus: Dictionary Filtering

Use the `auto_census` dictionary to filter and find people who match certain criteria:

- Create an empty list called `young_irish`
- Loop through the `auto_census` dictionary and add the names of people who are both from Ireland AND under 30 years old to your list
- Print the list of young people from Ireland and then print how many people match this criteria

### Bonus: Age Statistics

Calculate age statistics from `auto_census`:

- What is the average (median) age of all people in the census?
- What is the average (mean) age of all people in the census?
- What is the oldest age in the census?
- What is the name of the person with the oldest age?

Hint: use Google to try and figure out how you would do some of these calculations with a specific package
