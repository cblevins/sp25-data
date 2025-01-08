---
title: Understanding Data & Spreadsheets
toc: true
toc_sticky: true
classes: narrow

---

## Introduction

Over the next several classes you will be learning how to analyze and visualize data. To get started, we need to understand how to approach a dataset. Today we are going to practice these skills using the following dataset: [Video Game Sales](https://www.kaggle.com/datasets/gregorut/videogamesales).

## Data Reconaissance

The most important step when approaching a potential source of data is to familiarize with the source itself. I am going to set a timer for **10 minutes**, during which you are going to explore the following dataset with your group and answer as many of the following questions as possible in [this Google Doc](https://docs.google.com/document/d/1sFi2eOTq9y3fJzwiGKaPBj00LxmMndxkscQR_JbpQhY/edit?usp=sharing). 

* What kind of information is contained in this dataset?
* Who created it?
* Where did the data come from originally? 
* How was it collected?

Debrief:

* What are some of the limitations of this dataset? 
* What should we keep in mind while working with it?

## Spreadsheets

Once you have a grasp on the basics of the data and how it was produced, now we can start to look at the data itself. The data is formatted as a spreadsheet, arguably one of the most common data formats you will come across. Spreadsheets can come in several different file types. For today, we're going to work in Google Sheets. Click [this link](https://docs.google.com/spreadsheets/d/1y7ijDS0_IR4BUAUN7JUixkS-hk4TaLYEWD505Cd1NnU/edit?usp=sharing) to access the above dataset in Google Sheets. 

*Make a copy of the Google Sheet by going to `File -> Make a copy` and use that copy for today.*

### Sorting and Filtering

**Sorting** a spreadsheet is a common task. This allows you to "read" a spreadsheet more easily. 

- Sort the spreadsheet in **ascending order by the `Year` a game was released** (oldest games at the top -> newest/most recent games at the bottom)

**Filtering** a spreadsheet allows you to only look at one particular part of the spreadsheet while "hiding" the rest of the data. This can be helpful if your dataset is quite long.

- Filter the spreadsheet so that you are **only** looking at games that fall under the `Genre` category of `Sports`. 
	- How many games are there for this category?
	- Once you are done, reset the filter by clicking `Select All`
- You can also combine multiple categories into one filter. Filter the `Platform` column so that you are **only** looking at the following kinds of Playstation games: `PS`, `PS2`, `PS3`, `PS4`
	- How many games are there for this combined category?
	- Once you have finished so that you are seeing all the data
	- Once you are done, reset the filter by clicking `Select All`

### Functions

- **Functions** are a way to change, modify, or calculate values based on the existing data in an individual cell. Note that all the `Sales` columns contain numbers that are actually formatted in the millions. This isn't immediately obvious from the spreadsheet so we're going to use a basic function to change the sales column by multiplying it by 1 million.
	- Double inside column L1 and type `NA_Sale_Update` to give our column a new name
	- Double click inside the cell L2 and type: `=G2*1000000` then hit enter.
	- You'll notice this cell is now updated
	- We can apply the same function to more than one cell without needing to retype it. For instance, we want to apply the same "multiply by 1,000,000" function to the other `Sales` columns. 
	- To do this, click once on the cell, hover over the bottom right corner of the cell until you see a `+` sign, then click, hold and drag your mouse to the **right** four additional columns until you reach cell P3. You'll notice that it automatically applied the same function to each of these cells, moving the function one column over each time. We now have updated figures for all five `Sales` Columns.
	- We can also repeat this drag function process for every row. But this might take awhile since we have 16,000+ rows. Instead, hover your mouse over the bottom right of the cell LP until you see the + sign, then double-click. Now it automatically applies your function all the way down the columns.
- There are a wide variety of **functions**. Let's practice a different function: `=CONCATENATE()` - which allows us to stitch together the content of different cells.
	- Notice that we don't have column names for our updated Sales columns for EU, JP, Other, and Global. We could type out individual names for each of them, but instead our goal is to automatically create new column names for the new columns we just created based on the same format we used for L column (`NA_Sale_Update`). 	- Double click inside cell `M1` and type: `=CONCATENATE(H1, "_Update")`. Hit enter and you'll see that it automatically stitched together two pieces of text: the title of column H1 (`EU_Sales`) and the word `_Update`.
	- Do the same "drag" process you did above to apply the same function to the column names immediately to the right all the way out to P1. 
- More functions practice:
	- Double-click in cell Q2 and use the `=SUM()` function to calculate the total Global sales of video games. [Help with function](https://support.google.com/docs/answer/3093669?hl=en).
	- Double-click in  cell Q3 and use the `=AVERAGE()` function to calculate the average sales for a video game in Japan. [Help with the function.](https://support.google.com/docs/answer/3093615?hl=en)

	



