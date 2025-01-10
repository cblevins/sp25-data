---
layout: page
title: Pandas 1
---

First create a new directory within your class folder `working-with-data` called `pandas-1`. Launch Jupyter Labs and create a new Jupyter Notebook in that folder with the filename: `pandas-1.ipynb`.

We're going to be working with census data collected about Colorado counties from 1900-1950. Download [this CSV file]({{site.baseurl}}/in-class/co-census-skinny.csv) and make sure it is in your `pandas-1` folder.

To replicate best coding practices, you're going to use alternating Markdown and Code cells in your Jupyter Notebook. Copy and paste each of the following steps into a new Markdown cell that documents in your own words what you're doing in the following code cell. Then insert a new code cell and write your Python code that completes the task for that step.

1. Import the pandas library (`import pandas as pd`)
2. Read in the contents of the CSV of Colorado census data and assign it to a variable `co_df` (ie. Colorado dataframe)
3. Show the first 10 rows of the `co_df` dataframe
4. Show a random sample of 5 rows from the `co_df` dataframe
5. Follow [Walsh's example](https://melaniewalsh.github.io/Intro-Cultural-Analytics/03-Data-Analysis/01-Pandas-Basics-Part1.html#:~:text=we%20can%20filter%20a%20pandas%20dataframe) to just filter/select census data from 1940 and assign it to a new variable called `co_df_1940`.
6. Apply the `max()` function to the `population` column of `co_df_1940` to find the largest number people counted in a single Colorado county in the 1940 census.
7. What county had the largest number of people in 1940? Hint: use filter/select in conjunction with your steps from the previous step (`max()` and the `population` column).
8. Use filter/select to create a new dataframe named `denver_df` that only has records from Denver.
9. Use `denver_df.plot('year', 'population')` to create a line graph of Denver's population growth between 1900-1950.

_Bonus Practice_:

- Save your line graph for Denver's population growth as a .png file
- Export a new CSV file that just contains records for Denver (`denver_df`) - see [Walsh's example](https://melaniewalsh.github.io/Intro-Cultural-Analytics/03-Data-Analysis/01-Pandas-Basics-Part1.html#:~:text=To%20output%20a%20new%20CSV%20file).
