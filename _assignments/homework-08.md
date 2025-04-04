---
title: Homework 08
toc: true
toc_sticky: true
classes: wide2
author_profile: false
---

## Overview

In this assignment, you'll synthesize some of the Python skills you've learned over the past month or so, including Pandas and Plotly. You'll be analyzing the opening of new businesses in Colorado during the 1940s.

Draw on the following tutorials:

- 💻 Walsh, [Pandas Basics Part 1](https://melaniewalsh.github.io/Intro-Cultural-Analytics/03-Data-Analysis/01-Pandas-Basics-Part1.html)
- 💻 Walsh, [Pandas Basics Part 2](https://melaniewalsh.github.io/Intro-Cultural-Analytics/03-Data-Analysis/02-Pandas-Basics-Part2.html)
- 💻 Walsh, [Pandas Basics Part 3](https://melaniewalsh.github.io/Intro-Cultural-Analytics/03-Data-Analysis/03-Pandas-Basics-Part3.html)
- 🐼 [Pandas Concepts]({{ "/modules/pandas-concepts" | relative_url }})
- 💻 [Introduction to Plotly]({{ "/modules/plotly-intro" | relative_url }})
- 💻 [Cleaning Excel Files]({{ "/modules/excel-cleaning" | relative_url }})

## The Data

First, get the necessary data files from our shared course repository:

- Open GitHub Desktop and select your course repository (`lastname-sp25-data-materials`)
- Click `Fetch origin` to check for updates
- Go to `Branch` → `Merge into current branch` → select `upstream/main` -> `Merge`
- Click `Push origin` to sync everything up
- Launch Jupyter Lab and navigate to the `week-10` folder

You should see a single Excel file that you will be working with: `co-new-businesses-1940s.xlsx`. Inside that Excel file, there are two separate sheets: `New CO Businesses` and `Cities 1940`.

- `New CO Businesses`: This is a subset of new businesses that were established in Colorado during the 1940s - a subset of data drawn from [this database](https://data.colorado.gov/Business/Business-Entities-in-Colorado/4ykn-tg5h/about_data).
- `Cities 1940`: this contains population statistics for Colorado cities in the 1940 Census.

### Import Libraries and Load Data

- Import the necessary libraries:

  - pandas (using the alias `pd`)
  - plotly.express (using the alias `px`)

- Load both sheets from the Excel file:
  - Create a variable called `businesses_df` to store the "New CO Businesses" sheet in the Excel file
  - Create a variable called `cities_df` to store the "Cities 1940" sheet in the Excel file
  - Use `pd.read_excel()` with the appropriate parameters

### Familiarize Yourself with the Data

Familiarize yourself with the data:

- Display a sample of 10 rows from each dataframe.
- Check the data types for the columns in each dataframe

## Data Cleaning and Preparation

### Cleaning column names

For both datasets, you want to clean and standardize the column names (headers):

- Change column names to all lowercase
- Replace any whitespace with an underscore (`_`) - ex. `some column` becomes `some_column`
- _Hint: Use `str.lower()` and `str.replace()`_
- Show the first 10 rows of your dataframe to make sure it worked

### Standardize and clean data for cities

- Standardize city names in the business data so that it **removes any trailing or leading whitespace** and **changes the values to all lowercase** (hint: use `.str.strip()` and `.str.lower()`)
- Show the first 10 rows of your dataframe to make sure it worked

## Categorize Cities

### Define your function

Create a function called `categorize_city_size` that does the following:

- Takes in a number that corresponds to the population for a city.
- Returns the following based on the size of the city:
  - `Small Town` if population is less than 1,000
  - `Medium Town` if population is between 1,000 to 5,000
  - `Large Town` if population is between 5,000 to 20,000
  - `City` if population greater than or equal to 20,000

### Apply the function

- Take your `cities_df` dataframe and add a new column called `city_category` that applies your function to the `total_population` column of the dataframe.
- _Hint: use `apply()`_
- Show the first 10 rows of your dataframe to make sure it worked

## Analyze Businesses by Year

Let's take a look at how many new businesses were formed in Colorado in each year during the 1940s:

### Calculate new businesses by year

Create a variable called `businesses_per_year` by:

- Counting the number of new businesses based on `year_entity_formed`
- _Hint: use `value_counts()` and `reset_index()`_
- Show the first 10 rows of your dataframe

### Visualize new businesses by y ear

Create a bar chart using Plotly Express showing new businesses per year:

- Set x-axis to the year
- Set y-axis to the number of new businesses
- Add an appropriate title and labels
- Display text on each bar
- Hint: Use `px.bar()`

## Analyze Businesses by City

Let's take a look at how many new businesses were formed in each Colorado city during the 1940s:

## Calculate number of new businesses by city

Create a new variable called `city_businesses` that contains:

- A dataframe with counts of the number of new businesses in each city
- _Hint: Use `value_counts()` and `reset_index()`_
- Show the first 10 rows of your dataframe

## Visualize new businesses by city

Create a bar chart with Plotly Express showing the top 10 cities with the most new businesses created during the 1940s:

- Filter to only show the top 10 cities (hint: use `.head()`)
- Set x-axis to `city`
- Set y-axis to `count`
- Add an appropriate title and labels

## Combine Business and City Data

We have two datasets, both of which contain information about Colorado cities. Let's combine the two into a single dataframe that contains both information about new businesses and their population in the 1940 census.

### Merge dataframes

Merge the two dataframes together:

- Create a new variable called `merged_df`
- Use `pd.merge()` on the `city_businesses` and `cities_df` dataframes
- Figure out which column is shared between the two to use as your "key" to merge them
- ⚠️ **Note: use the `how='inner'` parameter for your merge**
- Show the first 10 rows of your new dataframe

### Filter out missing values

You'll note that several rows of data contain `NaN` or missing values - this means that there was a city listed in the businesses dataframe but it didn't have a corresponding match in the population dataframe. For now, remove these from the `merged_df` dataframe:

- Filter out rows where `total_population` is NaN
- _Hint: use a filter + `.notna()`_

### Calculate new businesses on a per capita rate

To make it easier to compare larger cities with smaller cities, you're going to calculate a new column for each city: the number of new businesses per 1,000 residents.

- Add a new column to `merged_df` called `biz_per_thousand` that is filled with:
  - A calculation dividing the `count` column by the `total_population` column and multiplying by 1,000
- Sort the merged dataframe by `biz_per_thousand` in descending order
- Show the first 10 rows of the dataframe to check if it worked

## Visualize new business creation by city

Let's say we want to see the cities with the highest _rate_ of business creation (ie. new businesses per thousand residents)

- Create a bar chart in Plotly of `merged_df`:
  - Filter to only show the top 10 cities (use `.head(10)`)
  - Set x-axis to `city`
  - Set y-axis to `biz_per_thousand`
  - Use `city_category` for color
  - Add an appropriate title and labels

## Bonus Challenge: New Businesses by City Category

Let's say we want to compare different size categories to see whether new businesses were cropping up in smaller places or bigger cities.

### Create a new dataframe

First, you'll need to create a new dataframe that consists of four rows, with each row a different category of city containing the total number of businesses created within that category of city.

- Create a new dataframe called `city_category_totals`
- Start with `merged_df`
- Group by `city_category`
- Add up (`sum()`) the `count` column
- Use `.reset_index()`

### Visualize businesses by city category

- Create a [pie chart](https://plotly.com/python/pie-charts/) in Plotly:

  - Use `px.pie()` with appropriate parameters
  - Use `city_category_totals` as your dataframe
  - Use `count` for your values
  - Use `city_category` for your names
  - Add an appropriate title and labels

## Bonus Challenge: Create a Scatter Plot

Create a scatter plot in Plotly showing:

- The relationship between city population (x-axis) and new businesses (y-axis)
- Only data for towns with a population of 2,000 or more people.
- Dots sized according to the number of new businesses in that city
- Dots colored according to their size category

## Submission Guidelines

- Run all code cells and make sure it is outputting without errors
- Submit both the notebook file (.ipynb) and a PDF export of your notebook
