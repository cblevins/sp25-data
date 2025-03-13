---
title: 🐼 Pandas Concepts
---

## The Basics: Spreadsheets in Python

Think about pandas like working with a spreadsheet:

- A **DataFrame** is the entire spreadsheet with both rows and columns (tables)
- A **Series** is just a single column from that spreadsheet (a list of values with labels)

## Working with Columns

Imagine we have the following table of data stored as a DataFrame in Python:

| name    | age | city     |
| ------- | --- | -------- |
| Alice   | 25  | New York |
| Bob     | 19  | Boston   |
| Charlie | 22  | Chicago  |
| Claire  | 18  | New York |

### Getting a Single Column (Series)

"Show me just the ages of all students":

```python
# This gives you just the 'age' column as a Series
ages = students['age']
```

Returns: A single column of data (a Series)

| age |
| --- |
| 25  |
| 19  |
| 22  |
| 18  |

### Getting Multiple Columns (DataFrame)

"I don't care about the city colun, give me a mini-spreadsheet of just names and ages"

```python
# This gives you both 'name' and 'age' columns as a DataFrame
name_and_age = students[['name', 'age']]
```

- Notice the **double brackets** `[[ ]]` - they're important!
- Returns: A mini-spreadsheet with the selected columns

| name    | age |
| ------- | --- |
| Alice   | 25  |
| Bob     | 19  |
| Charlie | 22  |
| Claire  | 18  |

## Working With Rows

### Filter Rows by Slicing

You'll often want to "filter" your dataframe, or create a shorter table with only a certain subset of rows. If you know how your rows are arranged sequentially, you can use a similar "slice" method as you've done for lists. If you only want the **first two rows of your dataframe** you would write:

```python
students[0:2]
```

This would return:

| name  | age | city     |
| ----- | --- | -------- |
| Alice | 25  | New York |
| Bob   | 19  | Boston   |

### Filtering Rows by a Condition

However, slicing is not as common with dataframes because they aren't always sequential (ie. the order of the rows doesn't matter). The more common way in which you'll end up filtering rows in a dataframe is by defining a "conditional". Let's say we have our full table of students but want to create a subset of this table of **only students over the age of 20.** So we'd essentially want Python to ask:

1. Is Alice's age > 20? **Yes** → Keep this row
2. Is Bob's age > 20? **No** → Remove this row
3. Is Charlie's age > 20? **Yes** → Keep this row
4. Is Claire's age > 20? **No** → Remove this row

Here's the code to apply this filter:

```python
students[students['age'] > 20]
```

| name    | age | city     |
| ------- | --- | -------- |
| Alice   | 25  | New York |
| Charlie | 22  | Chicago  |

Let's break our code `students[students['age'] > 20]` into two parts to make it easier to understand.

**Part 1: Build our filter**

`students['age'] > 20`: This part of the code tells Python to check each row in the entire `students` dataframe and ask "is the value in the `age` column greater than 20?" You can visualize this process a bit like this:

| name    | age | city     | ... | Did it meet our condition? |
| ------- | --- | -------- | --- | -------------------------- |
| Alice   | 25  | New York | ->  | 👍                         |
| Bob     | 19  | Boston   | ->  | ❌                         |
| Charlie | 22  | Chicago  | ->  | 👍                         |
| Claire  | 18  | New York | ->  | ❌                         |

Pandas generates a **Series** (like a list) made up of `True` or `False` values for every row depending on whether it meets our condition:

| 0 | True |
| 1 | False |
| 2 | True |
| 3 | False |

**Part 2: Apply the filter to the dataframe**

`students[...our filter...]`: This looks at the entire dataframe, feeds it our **Series** of `True`/`False` values, and uses it to only select rows where the answer to our condition is `True`.

## Grouping and Summarizing Data

Grouping data in Pandas divides up the rows in your dataframe and lumps them into separate buckets based on shared characteristics. You can then perform "summarize" features about these groups by performing calculations, observations, etc.

Let's take the analogy of **doing laundry**:

- Your hamper is filled with a jumbled up pile of different pieces clothing - ex. t-shirts, jeans, sweaters, socks, etc. All of your pieces of clothing have characteristics - color, fabric type, etc.
  - This like your starting dataframe, with each row as an individual piece of clothing and each column a characteristic about that piece of clothing.
- To do your laundry, you might want to group similar items together based on certain shared characteristics. You have a few options:
  - You could sort by **color** in order to keep your dark-wash jeans from bleeding into your nice white t-shirts. In this case, you'd you put your whites in one pile and your darks in another another pile.
  - You could sort by **fabric type** if you need to usedifferent dryer settings. In this case, you'd put your delicates that need low heat into one pile and your more durable clothes into another pile.
- Once your laundry is sorted into groups, you might "summarize" each of your groups by making observations about them:
  - "My darks pile is a lot bigger than my whites pile this week"
  - "I only have two items in my delicates pile, I guess I could wait to wash them until I have more..."

## Grouping Data

The `.groupby()` function in Pandas is the primary way to take your data and put it into separate buckets to analyze. Let's take a starting dataframe called `students`:

<!--
| name    | age | city     | grade |
| ------- | --- | -------- | ----- |
| Alice   | 25  | New York | 85    |
| Bob     | 19  | Boston   | 72    |
| Charlie | 22  | New York | 90    |
| Claire  | 18  | Chicago  | 78    |
| Emma    | 24  | New York | 88    |
| Frank   | 20  | Boston   | 79    |
-->

| row | name    | age | city     | grade |
| --- | ------- | --- | -------- | ----- |
| 0   | Alice   | 25  | New York | 85    |
| 1   | Bob     | 19  | Boston   | 72    |
| 2   | Charlie | 22  | New York | 90    |
| 3   | Claire  | 18  | Chicago  | 78    |
| 4   | Emma    | 24  | New York | 88    |
| 5   | Frank   | 20  | Boston   | 79    |

We could group each student according to the city where they are from:

1. **New York group**: Alice, Charlie, Emma
2. **Boston group**: Bob, Frank
3. **Chicago group**: Claire

The code to do this would be:

```python
students.groupby('city')
```

Pandas is doing several important things behind the scenes with this code:

- Identifies all the **unique values** in the dataframe's `city` column (`New York`, `Boston`, and `Chicago`)
- Rather than modifying the original dataframe or creating new data, Pandas creates **"virtual groups"** that point back to the corresponding rows in the `students` dataframe.
  - "New York" group → points back to **rows 0, 2, 4** in the original dataframe
  - "Boston" group → points back to **rows 1, 5** in the original dataframe
  - "Chicago" group → points back to **row 3** in the original dataframe
- Within each group, the original row order is preserved. So in the "New York" group, Alice (row 0) comes before Charlie (row 2) who comes before Emma (row 4), matching their order in the original dataframe.

## Summarizing Groups

Once our data is in groups, we usually want to "summarize" or calculate something about each group. This is where aggregation functions come in. They are applied to an entire column and can help us answer questions like:

- How many students are from each city?
- What's the average age of students from each city?

### Counting

Let's start with the first question. If we apply `.count()` to our grouped data, it might seem like we would write the following:

```python
city_groups=students.groupby('city')
city_groups.count()
```

But this means that you are telling Python to count up all the values ("non-null" values, specifically) _for each column_ in our grouped data, except the grouping column itself ('city').

| city     | name | age | grade |
| -------- | ---- | --- | ----- |
| Boston   | 2    | 2   | 2     |
| Chicago  | 1    | 1   | 1     |
| New York | 3    | 3   | 3     |

This is why it's often better to specifically select one column when using `.count()` after a groupby operation:

```python
city_groups=students.groupby('city')
city_groups['name'].count()
```

| city     | count |
| -------- | ----- |
| New York | 3     |
| Boston   | 2     |
| Chicago  | 1     |

### Average

If we wanted the answer to: what's the average age of students from each city? We could use `.mean()` (ie. average) for our `age` column in our city groups:

```python
city_groups=students.groupby('city')
city_groups['age'].mean()
```

This would give us the average ages of our students from each city:

| city     |      |
| -------- | ---- |
| New York | 23.7 |
| Boston   | 19.5 |
| Chicago  | 18.0 |

## Applying Functions to Dataframes

Oftentimes you want to take each individual value in a column and do something to it - change its contents, use it to calculate a new value, etc. This is where Pandas' `.apply()` comes in. In this case, you **define** a function then use `.apply()` to feed every individual value in a column into that function.

It can be confusing distinguishing between the built-in summary functions above (ex. `.mean()`, `.count()`, etc.) vs. `.apply()`. The main difference is that the summary functions act typically act on **a column as a whole** to aggregate or collapse all the values into a single "summary" (a number, value, etc.), whereas you are using `.apply()` on individual cells/values in a column.

### How .apply() Works: Breaking It Down

Let's start with our familiar students dataframe:

| name    | age | city     | grade |
| ------- | --- | -------- | ----- |
| Alice   | 25  | New York | 85    |
| Bob     | 19  | Boston   | 72    |
| Charlie | 22  | New York | 90    |
| Claire  | 18  | Chicago  | 78    |
| Emma    | 24  | New York | 88    |
| Frank   | 20  | Boston   | 79    |

Let's say we want to add a **new column** to the dataframe that flags students who might be struggling based on their grade.

We'd start by defining a custom function that takes a number grade and returns either `Doing Okay` or `Needs Help` based on this 80-point threshold.

```python
def grade_status(grade):
    if grade >= 80:
        return 'Doing Okay'
    else:
        return 'Needs Help'
```

The next step is to `.apply()` this function specifically to the `grade` column of the `students` dataframe:

```python
students['grade'].apply(grade_status)
```

And finally, we need to create a new column called `grade_flag` and "fill" that column with values that are returned from our function for every `grade` value:

```python
students['grade_flag']=students['grade'].apply(grade_status)
```

Let's break down what's happening:

- Python looks at EVERY single grade in the 'grade' column
- It runs each individual grade through our `grade_status()` function
- It creates a new column with the results:

| name    | age | city     | grade | grade_status |
| ------- | --- | -------- | ----- | ------------ |
| Alice   | 25  | New York | 85    | Doing Okay   |
| Bob     | 19  | Boston   | 72    | Needs Help   |
| Charlie | 22  | New York | 90    | Doing Okay   |
| Claire  | 18  | Chicago  | 78    | Doing Okay   |
| Emma    | 24  | New York | 88    | Doing Okay   |
| Frank   | 20  | Boston   | 79    | Needs Help   |

### Tips

- Your custom function should always:
  - Take one input (the individual item from the column)
  - Return something based on that item
- Your function takes in one input (ex. a single _value_ in a column), but you point `.apply()` on an _entire column_ or columns.
- You can use `.apply()` with built-in Python functions or with functions that you create yourself
