---
title: Mapping with Folium II
---

## Overview

In this tutorial you will apply the lessons you've learned in Pandas, Folium, and Plotly to map a new dataset. You might want to draw from:

- 💻 [Mapping with Folium I]({{ "/modules/mapping-folium-1" | relative_url }})
- 💻 [Introduction to Plotly]({{ "/modules/plotly-intro" | relative_url }})
- 🐼 [Pandas Concepts]({{ "/modules/pandas-concepts" | relative_url }})

## The Dataset

You are going to start from scratch and try to analyze and map a new historical dataset: `1877-official-register.csv`. This comes from the _Official Register of the United States_, for 1877. This is a bi-annual directory of workers employed by the federal government, listing their location (state and county) and salary for that year. Unlike a similar dataset you worked with in 💻 [Mapping with Folium I]({{ "/modules/mapping-folium-1" | relative_url }}), this dataset is made up of all other kinds of government employees besides postmasters. Note: this only includes data for western states and territories.

## Tasks

- Explore the basic contents of the dataset
- Make a map showing the locations of these employees
- Add popup/tooltip options that show the name of the location, the government agency, and the number of people working there
- Create another map where locations are sized according to the number of people employed there.
- Adjust sizes of the markers by creating categories and marker sizes
- Draw on your Pandas and Plotly skills to look at and visualize other dimensions of the data:
  - What were the top 10 individual **locations** measured by the largest number of employees?
  - Which **states** had the most government employees working in the state?
  - Which government **departments** employed the largest number of people?
  - How many different locations of government employees did each state have?
