---
title: Pandas Practice II
---

## Overview

In today's tutorial, you will be working in small groups to conduct data analysis on real historical datasets. This hands-on activity will help you apply the Pandas concepts you've been learning while exploring new datasets. Rather than have you try to just mimic what I'm doing as your instructor, this group-based activity will have you _apply_ what you've learned and think more creatively about how to use these skills.

Each group will be assigned one dataset to analyze. Your goal is to explore the data, develop interesting questions, and use Pandas to discover answers and insights. At the end of the session, your group will briefly share your most interesting finding.

## Get the Data

- Open GitHub Desktop and select your course repository (`lastname-sp25-data-materials`)
- Click `Fetch origin` to check for any changes
- Go to Branch → `Merge into current branch` → select `upstream/main` and click `Create a merge commit` if there are updates
- Click `Pull origin` if it's available (if not, you're up to date!)
- Click `Push origin` to sync everything up
- Launch Jupyter Labs and navigate to this week's folder
- You should see four `.csv` data files - each group will be assigned one of these datasets
- Create a new Jupyter Notebook in this week's folder with the filename: `yourlastname-pandas-3.ipynb`

## The Data

I've pre-selected several datasets. To learn more about what information they contain and how that information is captured, use the links below:

1. [`nobel_winners.csv`](https://github.com/rfordatascience/tidytuesday/tree/06bca976827f922af8c1f62db67e6c1a7f0dcd4b/data/2019/2019-05-14#nobel_winnerscsv)
2. [`jobs_gender.csv`](https://github.com/rfordatascience/tidytuesday/tree/06bca976827f922af8c1f62db67e6c1a7f0dcd4b/data/2019/2019-03-05#data-dictionary-1)
3. [`olympics.csv`](https://github.com/rfordatascience/tidytuesday/tree/06bca976827f922af8c1f62db67e6c1a7f0dcd4b/data/2021/2021-07-27#olympicscsv)
4. [`baby-names.csv`](https://github.com/hadley/data-baby-names/tree/master). Note: this particular dataset has a bit less documentation - to help you out, the `percent` column refers to the relative value of that name for that gende, for that year. Ex. if `John` has `0.07` percent in `1905`, that means babies named `John` made up `7%` of all male babies born that year.

## Steps for Analysis

### Initial Data Exploration

- Import the necessary libraries (pandas, matplotlib)
- Load your chosen dataset
- Refer to the original data sources (above) and try to figure out what kind of information is stored and how it is stored
- Examine the dataset structure using:
  - `.head()` to view the first few rows
  - `.info()` to understand columns and data types
  - `.describe()` to see statistical summaries
  - `.shape` to see dimensions
  - Check for missing values with `.isna().sum()`

### Brainstorm Questions

- As a group, brainstorm **three questions** you could answer with this data
- Focus on questions that might reveal interesting patterns or stories
- Document your brainstormed list of questions in a markdown cell
- Choose one of your questions to start with

### Analysis & Visualization

- Use Pandas methods to analyze your data and answer your questions - refer to Walsh's [Pandas Basics 1](https://melaniewalsh.github.io/Intro-Cultural-Analytics/03-Data-Analysis/01-Pandas-Basics-Part1.html) and [Pandas 2](https://melaniewalsh.github.io/Intro-Cultural-Analytics/03-Data-Analysis/02-Pandas-Basics-Part2.html)
- Create any new columns that might help answer your questions
- Filter, group, sort, or aggregate data to get closer to your answers
- Create at least one visualization to illustrate your findings
- Use markdown cells to explain your process and interpret results

### Class Debrief

- What was the most interesting or surprising finding?
- What challenges did you encounter in the analysis?
- What additional data would help you answer your questions better?

## Collaboration Tips

- Take turns writing code
- If someone is stuck, work through the problem together instead of taking over
- Document your thought process in markdown cells
- When you encounter errors, read them carefully and try to debug together
- This should be an iterative process! It's normal to refine your questions as you learn more about the data, and you might need to try several approaches before finding something interesting.
