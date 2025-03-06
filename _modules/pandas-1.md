---
title: Pandas Practice I
---

## Get Started

- Open GitHub Desktop and select your course repository (`lastname-sp25-data-materials`)
- Click `Fetch origin` to check for any changes
- Go to Branch → `Merge into current branch` → select `upstream/main` and click `Create a merge commit` if there are updates
- Click `Pull origin` if it's available (if not, you're up to date!)
- Click `Push origin` to sync everything up

## Pandas Practice

- Launch Jupyter Labs and navigate to this week's folder
- Create a new Jupyter Notebook in this week's folder with the filename: `yourlastname-pandas-1.ipynb`.
- We are going to be working with census data from the state of Colorado between 1900-1950. This is contained in the file: `co-census-skinny.csv`
- Complete the following steps:

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

- Save your line graph for Denver's population growth as a `.png` file
- Export a new CSV file that just contains records for Denver (`denver_df`) - see [Walsh's example](https://melaniewalsh.github.io/Intro-Cultural-Analytics/03-Data-Analysis/01-Pandas-Basics-Part1.html#:~:text=To%20output%20a%20new%20CSV%20file).
