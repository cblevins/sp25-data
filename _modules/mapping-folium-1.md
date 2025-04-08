---
title: Mapping with Folium
---

## Overview

This tutorial will guide you through the process of creating interactive maps using Python's Folium library. We'll be working with a historical dataset of post offices and postmaster salaries from Utah in 1871 to visualize geographic data. The tutorial draws on steps laid out in Melanie Walsh's tutorial [Making Interactive Maps](https://melaniewalsh.github.io/Intro-Cultural-Analytics/07-Mapping/01-Mapping.html#making-interactive-maps).

This data was compiled by Prof. Blevins while working on his book. It comes from the _Official Register of the United States_ for 1871. This is a bi-annual directory of workers employed by the federal government, listing their location (state and county) and salary for that year.

## Getting Set Up

First, let's install the necessary libraries and import them for our mapping project.

```python
#if you have not installed folium yet:
#!pip install folium

import folium
import pandas as pd
```

Let's load our historical dataset and take a quick look at its structure. Note that it has `Latitude` and `Longitude` coordinates - this means we can place these points on a map.

```python
utah_df = pd.read_csv('1871-utah-postmaster-salaries.csv')
print(utah_df.sample(5))
utah_df.dtypes
```

## Creating a Base Map

The first step in folium is to create our "base map," or the map layer that we are going to add data on top of. Let's create a simple map centered on Utah:

```python
utah_map_empty = folium.Map(location=[40, -111], zoom_start=6)
utah_map_empty
```

## Creating a Reusable Function for Maps

One tricky part of Folium is that your map is stored in local memory and every time you add data to it, that data continues to stay on the map. If you're running multiple code cells, trying things out, etc. this means you are constantly layering more and more data onto it. Instead, we'd like to be able to "wipe the slate clean" and start fresh each time with a blank base map. To do that, we're going to create a function that generates an empty map that we can reuse each time:

```python
def create_empty_map():
    return folium.Map(location=[40, -111], zoom_start=6)

utah_map = create_empty_map()
utah_map
```

### Checking for Missing Data

Before adding post offices to our map, let's check which locations might have missing coordinate data. This means that we don't actually know where the post office was located, and therefore cannot add it to a map.

```python
# Check for columns with missing values
missing_values = utah_df.isna().sum()
print(missing_values)
```

It looks like we have four missing locations, so let's remove these post offices from our dataset and check to make sure that the two dataframes now have a different number of rows:

```python
# Filter out post offices that are missing a latitude value (ie. we don't have any location information about it)
utah_df_locations = utah_df[utah_df['Latitude'].notna()]
print(len(utah_df))
print(len(utah_df_locations))
```

## Adding Points to Our Map

### Adding a Single Marker

It helps to start small and build up. To begin, let's try manually adding a single first marker to the map to represent a single post office from our dataset:

```python
folium.Marker(location=[38.41, -112.339], popup="Adamsville Post Office").add_to(utah_map)
utah_map
```

## Defining a Marker Creation Function

Instead of adding a single marker manually, we're going to write a function based on this command that takes in a row of data and uses it to add a single marker to the map automatically.

```python
# Melanie Walsh function we will adadpt to our dataset:
# def create_map_markers(row, map_name):
#    folium.Marker(location=[row['lat'], row['lon']], popup=row['place']).add_to(map_name)

def create_map_markers(row, map_name):
    folium.Marker(location=[row['Latitude'], row['Longitude']], popup=row['PO_Name']).add_to(map_name)
```

Let's test it out using a random sample row (ie. a single post office) from our actual dataset

```python
#create a base empty map
utah_map = create_empty_map()

#generate a random row of data
sample_row = utah_df_locations.sample(1)

#use our function on the random row
create_map_markers(sample_row, utah_map)

#display the map
utah_map
```

### Method 1: Adding Markers Using a For Loop

Now that we've written a function, we can apply it to our entire dataframe in several different ways. The first way is using a traditional for loop approach. This moves sequentially through our dataset and adds each row of data to the map. This method is less efficient, but it helps to conceptualize the process of what our function si doing:

```python
# Method 1: Using a for loop to iterate through our dataframe and add markers sequentially
# initialize an empty map
utah_map = create_empty_map()

# iterrows() allows you to loop through a dataframe row by row and return the index position + the row
for index, row in utah_df_locations.iterrows():
    print(f"Name of post office:", row[0])

#now let's iterate through and call our function for each row
for index, row in utah_df_locations.iterrows():
    create_map_markers(row, utah_map)

utah_map
```

### Method 2: Adding Markers Using `apply()`

The more common way of using functions with pandas dataframes is to use the `apply()` function. Note that to do this, you'll need to include a few additional parameters which I've explained in the code below:

```python
# Method 2: Using .apply() to add markers with our function for all rows
# initialize an empty map
utah_map = utah_map_empty

# Now apply this function to each row in our filtered DataFrame
# For each row, we'll pass:
# 1. The row itself (handled automatically by .apply())
# 2. Our map object (we need to specify this explicitly)
# 3. The "axis" value for .apply() to indicate we want to process row by row
# .apply() allows you to apply a function to each row in the dataframe
utah_df_locations.apply(
    create_map_markers, # The function to apply
    map_name=utah_map, # Additional argument to pass to the function
    axis='columns' # Process row by row instead of column by column
)

utah_map
```

## Creating Circle Markers

### Create a Function for Circle Markers

Our first step is to make a new function to add circle markers to a map. Note the new variables you can adjust: the `radius` of hte cirlce (ie. how big it is), or the `fill` (whether it's filled with a color or empty).

```python
# Melanie Walsh function we will edit:
#def create_ICE_map_markers(row, map_name):
#    folium.CircleMarker(location=[row['lat'], row['lon']], raidus=100, fill=True,
#                       popup=folium.Popup(f"{row['Name'].title()} <br> {row['City'].title()}, {row['State']}", max_width=200),
#                       tooltip=f"{row['Name'].title()} <br> {row['City'].title()}, {row['State']}"
#                       ).add_to(map_name)

def create_circle_markers(row, map_name):
    folium.CircleMarker(location=[row['Latitude'], row['Longitude']],
                       radius=200,
                       fill=True,
                       popup=folium.Popup(f"{row['PO_Name'].title()}", max_width=200),
                       tooltip=f"{row['PO_Name'].title()}"
                       ).add_to(map_name)
```

### Adding Circle Markers to the Map

Now let's apply our circle marker function to all locations:

```python
# initialize an empty map
utah_map = create_empty_map()

# call our function for each row
utah_df_locations.apply(create_circle_markers, map_name=utah_map, axis="columns")

utah_map
```

### Customizing Marker Appearance

You'll see that we should adjust some of our variables for the map's appearance.

```python
# alter map appearance
def create_circle_markers(row, map_name):
    folium.CircleMarker(location=[row['Latitude'], row['Longitude']],
                       radius=14,
                       color='green',
                       fill=True,
                       fill_color='green',
                       fill_opacity=0.2,
                       popup=folium.Popup(f"Post Office: {row['PO_Name'].title()}", max_width=200),
                       tooltip=f"Postmaster Salary: ${row['PM_Salary']}"
                       ).add_to(map_name)

# initialize an empty map
utah_map = create_empty_map()

# call our function for each row
utah_df_locations.apply(
    create_circle_markers, # The function to apply
    map_name=utah_map, # Additional argument to pass to the function
    axis='columns' # Process row by row instead of column by column
)

utah_map
```

### Make Your Own Adjustments

Create a new code block, copy and paste the above code, and then experiment to make the following adjustments:

- Make the cirlces smaller
- Make the color and fill of the circles red instead of green
- Make them a little less transparent

## Creating Markers Sized by Salary

One of the benefits of using circle markers is that we can dynamically adjust their size to visualize different information. The main data we have attached to each post offiecs is the **annual salary of the postmaster at that office in 1871.** Let's create a map where instead of location markers we have circles, with the size of the circle corresponding to the postmaster's salary.

### Using a Function to Size the Circles

Let's make our visualization more informative by sizing the markers according to postmaster salary. The main code that this is `radius=row['PM_Salary']` - this means that the value for the size of the marker in (measured in **pixels**) corresponds directly to value of the `PM_Salary` column (measured in **dollars**). Ex. a salary of `150 dollars` translates into a circle on the map with a radius of `150 pixels`.

```python
# make new function to create circle markers sized by postmaster salary
def create_sized_circle_markers(row, map_name):
    folium.CircleMarker(location=[row['Latitude'], row['Longitude']],
                       radius=row['PM_Salary'],
                       fill=True,
                       popup=folium.Popup(f"Post Office: {row['PO_Name'].title()}", max_width=200),
                       tooltip=f"Postmaster Salary: ${row['PM_Salary']}"
                       ).add_to(map_name)

# initialize an empty map
utah_map = create_empty_map()

# call our function for each row
utah_df_locations.apply(
    create_sized_circle_markers, # The function to apply
    map_name=utah_map, # Additional argument to pass to the function
    axis='columns' # Process row by row instead of column by column
)

utah_map
```

## Adjusting Marker Sizes for Better Visibility

The direct salary values make some markers too large, so let's scale them down for better visibility. One rough way to do this is to simply divide all the values for the postmaster salary by 100.

```python
# make new function to create circle markers sized by postmaster salary - this time adjusting the radius size in pixels to make it more legible
def create_sized_circle_markers(row, map_name):
    folium.CircleMarker(location=[row['Latitude'], row['Longitude']],
                       radius=row['PM_Salary']/100,
                       fill=True,
                       popup=folium.Popup(f"Post Office: {row['PO_Name'].title()}", max_width=200),
                       tooltip=f"Postmaster Salary: ${row['PM_Salary']}"
                       ).add_to(map_name)

# initialize an empty map
utah_map = create_empty_map()

# call our function for each row
utah_df_locations.apply(
    create_sized_circle_markers, # The function to apply
    map_name=utah_map, # Additional argument to pass to the function
    axis='columns' # Process row by row instead of column by column
)

utah_map
```

## Categorizing Salaries Into Buckets

The method of simply translating dollars into pixels is not all that sophisticated. Instead, let's create a new category for our dataset that creates categories or "buckets" of post offices based on their postmaster salary.

To start, we can examine the statistical distribution of our dataset to look at the PM_Salary column and get a sense for the distribution of different values:

```python
utah_df_locations.describe()
```

### Function to categorize salary data

Next, we'll create a function that takes in a number and returns a string value for a category.

```python
def add_salary_buckets(salary):
    # Create a new column for the salary bucket
    if salary < 50:
        bucket = 'Low Salary'
    elif salary >= 50 and salary < 250:
        bucket = 'Medium Salary'
    elif salary >= 250 and salary < 1000:
        bucket = 'High Salary'
    else:
        bucket = 'Very High Salary'
    return bucket
```

To make sure it's working, let's just use a single number on it. Try out a few different values from the different categories:

```python
#test out the function
add_salary_buckets(2000)
```

Now let's apply it to the entire dataframe, creating a new column called `Salary_Bucket` to fill in these new salary categories.

```python
utah_df_locations['Salary_Bucket'] = utah_df_locations['PM_Salary'].apply(add_salary_buckets)
utah_df_locations.head()
```

### Creating Marker Sizes Based on Salary Categories

Similarly, we are going to add another column to the dataframe that we can use to tell Folium what size marker to use for that post office (based on its salary category).

```python
# create a function to add marker sizes based on the salary bucket
def add_marker_sizes(category):
    if category == 'Low Salary':
        return 4
    elif category == 'Medium Salary':
        return 8
    elif category == 'High Salary':
        return 12
    else:
        return 16

#test out the function
add_marker_sizes('High Salary')
```

Apply the function to the whole dataframe to create a new column:

```
utah_df_locations['Marker_Size'] = utah_df_locations['Salary_Bucket'].apply(add_marker_sizes)
utah_df_locations.head(10)
```

## Visualizing Postmaster Salaries by Category

Finally, let's create our map with markers sized according to salary categories. Note that `radius` is now being defined by the new `Marker_Size` column:

```python
# make new function to create circle markers sized by salary category
def create_sized_circle_markers(row, map_name):
    folium.CircleMarker(location=[row['Latitude'], row['Longitude']],
                       radius=row['Marker_Size'],
                       fill=True,
                       opacity=0.6,
                       popup=folium.Popup(f"Post Office: {row['PO_Name'].title()}", max_width=200),
                       tooltip=f"Postmaster Salary: ${row['PM_Salary']}"
                       ).add_to(map_name)

# initialize an empty map
utah_map = create_empty_map()

# call our function for each row
utah_df_locations.apply(
    create_sized_circle_markers, # The function to apply
    map_name=utah_map, # Additional argument to pass to the function
    axis='columns' # Process row by row instead of column by column
)

utah_map
```

## Your Turn: Map a New Dataset

Use the above steps to start from scratch and try to map a different historical dataset: `1877-official-register.csv`. This comes from a similar source: the _Official Register of the United States_, but from a few years later (1877). Rather than focusing on postmasteers, this dataset is made up of other kinds of government employees.

Your goal:

- Explore the contents of the dataset
- Make a map showing the locations of these employees
- Add popup/tooltip options that show the name of the location, the government agency, and the number of people working there
- Create another map where locations are sized according to the number of employees there.
- Adjust sizes of the markers by creating categories and marker sizes
