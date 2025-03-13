---
title: Pandas Practice III
---

## Overview

We're going to work the following dataset: [Census of Utah Territory, 1880](https://www.icpsr.umich.edu/web/ICPSR/studies/8879). This dataset contains census information about people living in Utah in the year 1880. Note: I've modified the dataset to make it more usable in Python.

## Get the Data

- Open GitHub Desktop and select your course repository (`lastname-sp25-data-materials`)
- Click `Fetch origin` to check for any changes
- Go to Branch → `Merge into current branch` → select `upstream/main` and click `Create a merge commit` if there are updates
- Click `Pull origin` if it's available (if not, you're up to date!)
- Click `Push origin` to sync everything up
- Launch Jupyter Labs and navigate to this week's folder
- You should see a file called `utah-census-1880.csv`
- Create a new Jupyter Notebook in this week's folder with the filename: `yourlastname-pandas-3.ipynb`

## Pandas

To replicate best coding practices, you're going to use alternating Markdown and Code cells in your Jupyter Notebook. Copy and paste each of the following steps into a new Markdown cell that documents in your own words what you're doing in the following code cell. Then insert a new code cell and write your Python code that completes the task for that step.

- Import the pandas library
- Read in the contents of the CSV of Utah census data and assign it to a variable `utah_df` (ie. Utah dataframe)
- Let's take a look at the contents of the dataframe. Since there are a lot of columns, copy and paste this code, which tells Python not to "truncate" the columns and instead show all of them: `pandas.set_option('display.max_columns', None)`. Then write a line of code to display a random sample of 12 rows from the dataframe.

---

> PAUSE: Take **3-5 minutes** to look at all of the columns and the sample rows. Think back to your readings the past few weeks on the US Census. How might you take some of the historical themes, takeaways, or lessons you've learned about the US Census and apply them _specifically to this dataset_? Insert a Markdown cell and use it to brainstorm as many observations and ideas as you can in 3-5 minutes.

---

- Look at the column `birthstate` and some of the values from your random sample. Change the name of the column to something more accurate.
- Replace the `NaN` values in the `occupation` column with the string: `Unknown`.
- Just isolate people who work on a farm in some capacity. Create a filter and subset the data using `str.contains` to return rows whose `occupation` contains `FARM`. How many people work on a farm?
- The three most common categories for `marrystatus` have been shortened to single letters. Write three lines of code that each uses `str.replace` on the `marrystatus` column to replace:
  - `m` with `married`
  - `s` with `single`
  - `w` with `widowed`
- Define a function called `birthyear_calc` to calculate the year an individual was born based on their `age` column and the year the census was recorded (`1880`) - note: this won't be perfect.
- Add a new column called `birthyear` that is populated with the same values as the `age` column. These are placeholder values that we are about to change.
- Use `apply` and your function `birthyear_calc` on the `birthyear` column to calculate new values for each person's birth year.
- 10. Use the following code to change the `birthyear` column to an Integer data type rather than a Float (decimal): `utah_df['birthyear']=utah_df['birthyear'].astype('int64')`
- 11. Use `groupby` to count the number of people living in Utah in 1880 who were born each year leading up to 1880. Assign this to a new variable `birthsbyyear`.
- 12. Plot a time series graph of `birthsbyyear` to chart how many people were born each year.
- 13. What explains the weird spikes in the graph?
