---
layout: page
title: Pandas III Practice
---

First create a new directory within your class folder `working-with-data` called `pandas-3`. Launch Jupyter Labs and create a new Jupyter Notebook in that folder with the filename: `pandas-3.ipynb`.

We're going to continue working with the dataset: [Census of Utah Territory, 1880](https://www.icpsr.umich.edu/web/ICPSR/studies/8879). I've modified the dataset to make it more usable in Python. Download [this CSV file]({{site.baseurl}}/in-class/utah-census-1880.csv) and make sure it is in your `pandas-3` folder.

To replicate best coding practices, you're going to use alternating Markdown and Code cells in your Jupyter Notebook. Copy and paste each of the following steps into a new Markdown cell that documents in your own words what you're doing in the following code cell. Then insert a new code cell and write your Python code that completes the task for that step.

1. Import the pandas library
2. Read in the contents of the CSV of Utah census data and assign it to a variable `utah_df` (ie. Utah dataframe)
3. Show a random sample of 10 rows from the dataframe
4. Look at the column `birthstate` and some of the values from your random sample. Change the name of the column to something more accurate.
5. Replace the `NaN` values in the `occupation` column with the string: `Unknown`.
6. Just isolate people who work on a farm in some capacity. Create a filter and subset the data using `str.contains` to return rows whose `occupation` contains `FARM`. How many people work on a farm?
7. The three most common categories for `marrystatus` have been shortened to single letters. Write three lines of code that each uses `str.replace` on the `marrystatus` column to replace:

- `m` with `married`
- `s` with `single`
- `w` with `widowed`

7. Define a function called `birthyear_calc` to calculate the year an individual was born based on their `age` column and the year the census was recorded (`1880`) - note: this won't be perfect.
8. Add a new column called `birthyear` that is populated with the same values as the `age` column. These are placeholder values that we are about to change.
9. Use `apply` and your function `birthyear_calc` on the `birthyear` column to calculate new values for each person's birth year.
10. Use the following code to change the `birthyear` column to an Integer data type rather than a Float (decimal): `utah_df['birthyear']=utah_df['birthyear'].astype('int64')`
11. Use `groupby` to count the number of people living in Utah in 1880 who were born each year leading up to 1880. Assign this to a new variable `birthsbyyear`.
12. Plot a time series graph of `birthsbyyear` to chart how many people were born each year.
13. What explains the weird spikes in the graph?
