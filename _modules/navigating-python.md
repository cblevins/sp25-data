---
title: Navigating Python
toc: false
---

Navigate to your `week-02` folder in your `lastname-sp25-data-materials` folder. Launch Jupyter Labs and create a new Jupyter Notebook in that folder with the filename: `navigating-python.ipynb`. Your goal today is to practice using variables to write some Python code that generates information about the historical figure **Lucy Parsons**.

To replicate best coding practices, you're going to use alternating Markdown and Code cells in your Jupyter Notebook. Copy and paste each of the following steps into a new Markdown cell that documents in your own words what you're doing in the following code cell. Then insert a new code cell and write your Python code that completes the task for that step.

1. Make new variables for the historical figure Lucy Parsons for her first name, last name, birth year, and the state in which she was born - use her [Wikipedia page](https://en.wikipedia.org/wiki/Lucy_Parsons).

2. Make a new variable `full_name`. Assign it a single string value based on the variables you created above. Then add a print statement that writes out a full sentence using `full_name`.

3. How old was Lucy Parsons during the Haymarket affair? Calculate her age using the variables you created above, and assign it to a new variable `haymarket_age`. End with a full-sentence print statement answering the question that uses `haymarket_age` and an f-string.

4. Lucy Parsons's contemporary and rival, Emma Goldman, also has [a Wikipedia page](https://en.wikipedia.org/wiki/Emma_Goldman). Create variables and assign each one the number of footnotes for each of their Wikipedia pages (you can do this manually). Create another variable calculating the **difference** between them. Then write a print statement that compares these two numbers in some way.

_Bonus Practice_:

- Google a common Python function and try to figure out how to use it to count how many **characters (ie. letters)** are in Lucy Parsons' full name.
- Go to [this page](https://python.omics.wiki/www/download-webpage) and try to adapt the code on this page to do the following:
  - Access the Lucy Parsons Wikipedia page (`# Python 3`)
  - Print the title of the Wikipedia page (`# extract webpage title`)
  - Download a copy of the page named `parsons.html` (`# save as local file 'webpage.html'`)
  - View the downloaded HTML file (`# read local file`)
- Look at the section on [Booleans in "Data Types" tutorial](https://melaniewalsh.github.io/Intro-Cultural-Analytics/02-Python/05-Data-Types.html#:~:text=72%20%25%2010-,Booleans,-%C2%B6) to determine if `first_name` and `birth_year` are the same data type.
