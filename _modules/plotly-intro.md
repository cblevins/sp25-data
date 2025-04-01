---
title: Introduction to Plotly
---

## Overview

In this tutorial, we'll learn how to create interactive visualizations using Plotly Express, a high-level visualization library built on top of Plotly. Plotly creates web-based visualizations that allow users to hover, zoom, and interact with the data in ways that static visualizations cannot.

We'll be using our now-familiar 1880 Utah Census data to explore various visualization techniques.

## Setup

- Use Github Desktop to sync up the shared class repository
- The Utah Census dataset can be found in your `week-09` folder `utah-census-1880.csv`
- Create a new Jupyter Notebook file in the `week-09` folder called `plotly-intro.ipynb`

First, let's import the libraries we'll need and load our dataset:

```python
# Import libraries
import pandas as pd
import plotly.express as px

# Set pandas display options
pd.options.display.max_rows = 50

# Load the Utah 1880 Census data
utah_df = pd.read_csv('utah-census-1880.csv')
```

Let's take a quick look at our data:

```python
# Examine sample of rows
utah_df.sample(10)
```

## Your First Plotly Visualization

Let's start with something simple - a bar chart showing the number of people by county. We'll first need to count the number of people in each county:

```python
# Count the number of people in each county
county_counts = utah_df['county'].value_counts()

# Display the counts
county_counts
```

For Plotly (and many other visualization libraries), we need the data in a column format rather than as an index. We can use the `reset_index()` function to convert the index into a regular column:

```python
# Apply reset_index() to convert the index (county names) into a regular column
county_counts = county_counts.reset_index()
county_counts.columns = ['county', 'count']

# Display the counts after reset_index
county_counts
```

The `reset_index()` function is essential when preparing grouped data for visualization, as it transforms the index values (in this case, county names) into a column that Plotly can use for the x-axis.

Now, let's create our first Plotly bar chart:

```python
# Create a simple bar chart
fig = px.bar(county_counts, x='county', y='count')

# Show the figure
fig.show()
```

Congratulations! You've created your first interactive Plotly visualization.

## Customizing Your Visualizations

Now let's customize our visualization to make it more informative and visually appealing.

Let's improve our chart by adding a title and better axis labels:

```python
# Add title and customize axis labels
fig = px.bar(
    county_counts,
    x='county',
    y='count',
    title='Population by County in Utah (1880)',  # Add a title
    labels={'county': 'County', 'count': 'Population'}  # Rename axis labels
)

# Display the chart
fig.show()
```

Now let's make the chart more visually appealing by adding a different color scale ([other options here](https://plotly.com/python/builtin-colorscales/)) and using a different visual template for a cleaner white background.

```python
# Add color and use a cleaner template
fig = px.bar(
    county_counts,
    x='county',
    y='count',
    title='Population by County in Utah (1880)',
    labels={'county': 'County', 'count': 'Population'},
    color='count',                     # Color bars by population
    color_continuous_scale='Inferno_r',  # Use a reversed color scale
    template='plotly_white'            # Use a clean white template
)

# Display the chart
fig.show()
```

Finally, we can adjust the layout to improve readability and appearance. We're going to update the layout (`.update_layout()`) with several options to adjust the axis titles and the dimensions of the visualization.

```python
# Add color and use a cleaner template
fig = px.bar(
    county_counts,
    x='county',
    y='count',
    title='Population by County in Utah (1880)',
    labels={'county': 'County', 'count': 'Population'},
    color='count',                     # Color bars by population
    color_continuous_scale='Inferno_r',  # Use a reversed color scale and the Inferno color scheme
    template='plotly_white'            # Use a clean white template
)

# Update layout with additional customizations
fig.update_layout(
    xaxis_title='County',                  # Customize x-axis title
    yaxis_title='Number of People',        # Customize y-axis title
    xaxis_tickangle=-45,                   # Rotate x-axis labels 45 degrees
    height=500,                            # Set chart height in pixels
    width=800,                             # Set chart width in pixels
    title_font=dict(size=22),              # Change title font size
    plot_bgcolor='white',                   # Set plot background color
    margin=dict(l=40, r=40, t=80, b=80),   # Adjust margins (left, right, top, bottom)
    showlegend=True,                       # Show the color scale legend
    legend_title_text='Population',        # Set legend title
    hoverlabel=dict(                       # Customize hover label appearance
        bgcolor="white",
        font_size=12,
        font_family="Arial")
)

# Display the chart
fig.show()
```

## Create Your Own Visualization

Now it's your turn to create a visualization using what you've learned. We'll make a simple bar chart showing the distribution of the top 10 occupations in the Utah 1880 census:

```python
# First, let's prepare our data
# Count the frequency of each occupation, take the top 10, and reset the index
top_occupations = utah_df['occupation'].value_counts().head(10).reset_index()
top_occupations.columns = ['occupation', 'count']

# Display the prepared data
top_occupations
```

Use what you've learned above to create an enhanced bar chart showing the top 10 occupations in the Utah Census that does the following across three code blocks:

1. Create a bar chart using `px.bar()` with:

   - x-axis showing occupation names
   - y-axis showing the count
   - Bars colored by count (to highlight the most common occupations)

2. Customize the chart with:

   - An appropriate title (e.g., "Top 10 Occupations in Utah (1880)")
   - Clear axis labels
   - A different [color scheme](https://plotly.com/python/builtin-colorscales/) from the code above
   - A template OTHER than `plotly_white`

3. Enhance the chart's appearance with `update_layout()`:
   - Rotate the x-axis labels if needed for readability
   - Adjust the chart dimensions (height: 400 and width: 800)
   - Customize the title font size to size 30
   - Set different margins from above
   - Add a legend and legend title
   - Customize the hover label appearance

## Bonus

- Export your chart as a static image and share it on the class Discord server

## Resources for Learning More

- [Plotly Express Documentation](https://plotly.com/python/plotly-express/)
- [Plotly Python Documentation](https://plotly.com/python/)
- [Plotly Express Cheat Sheet](https://images.plot.ly/plotly-documentation/images/plotly_express_cheat_sheet.pdf)
- [Plotly Community Forum](https://community.plotly.com/)
