---
title: Using Generative AI as a Coding Partner
---

## Overview

In this tutorial, you're going to practice using Generative AI tools as coding partners to help you work with historical data.

## Data and Context

For this exercise, we'll be working with the [Frederick Bee History Project website](https://www.frederickbee.com/femalerecords.html), which contains a number of historical records collected by Anthony Ortel documenting the life and work of Frederick Alonzo Bee (1825-1892). Bee served as a consul at the Chinese consulate in San Francisco from 1878 to 1892 where he advocated for the civil rights of Chinese immigrants.

The larger context for Frederick Bee is that he was working during a period of extreme anti-Chinese sentiment in the United States. The Page Act of 1875 restricted immigration of Chinese women into the United States by classifying many of them as prostitutes. Even more infamously, in 1882 Congress passed the Chinese Exclusion Act, which prohibited all immigration of Chinese laborers. A major part of Bee's legal work involved filing writs of habeas corpus for Chinese immigrants who had lived in the United States before the restrictions went into effect, had temporarily left the country, and were then denied re-entry and wrongfully imprisoned by immigration authorities upon their return.

Ortel's website exemplifies a common type of documentary project you might find online, in which a passionate researcher, geneaologist, or enthusiast has collected a tremendous amount of valuable historical information on a specific subject. In this case, Ortel has compiled records related to Bee's life, including census data, legal cases, and other primary source documents from the late 19th century. However, as digital researchers this kind of website poses a challenge: it was built and organized for a human reader to peruse. This means that most of its information is stored in formats (ie. webpages) that aren't amenable to digital analysis.

In this tutorial, you are going to be using Generative AI for a number of tasks to process and analyze some of the data from the Frederick Bee History Project.

## Get Set Up

Before we begin, let's set up a new Jupyter Notebook to document our work:

- Navigate to your `week-12` folder in your course materials repository
- Open Jupyter Lab or Jupyter Notebook
- Create a new notebook named `lastname-ai-coding-partner.ipynb` (replace "lastname" with your actual last name)

## Converting HTML Pages to Structured Tabular Data

### Exploring the Data Source

Visit the following page: [records of female detainees whose cases were adjudicated at the US District Court for the Northern District of California, San Francisco from 1882 to 1892.](https://www.frederickbee.com/femalerecords.html). Spend a few minutes exploring the page as a researcher.

- What kind of information is on this page? What is it showing?
- What would this page look like if it was transformed into a tabular dataset (ie. CSV file)?
- What challenges do you see for extracting this information into a tabular dataset?

### Using AI to Develop an Extraction Strategy

We're going to use ChatGPT to develop a plan for converting this HTML page into a structured CSV file.

- Although these models can follow web links, oftentimes it is more straightforward to upload files directly.
- I've provided a downloaded HTML file of the page in your `week-12` folder named `female-detainee-cases.html` (or right-click [this link]({{ "/modules/female-detainee-cases.html" | relative_url }}) and click Save as...)
- It's also easy to generate this yourself. Go to <https://www.frederickbee.com/femalerecords.html>, right click somewhere on the page, then look for an option of `Save as...` and save the file as an HTML file in your `week-12` folder named `female-detainee-cases.html`.

Now that you have a local copy of the website, open ChatGPT and select `o4-mini-high` mode. This will activate the "reasoning" mode for the model. Upload the HTML file and copy and paste the following prompt:

> I'm trying to extract data from the attached HTML file that contains records of female detainees whose cases were adjudicated at the US District Court for the Northern District of California, San Francisco from 1882 to 1892. Examine the contents of the file and how it is structured, then come up with a step by step plan to use Python to turn its contents into a CSV tabular dataset. First give a broad overview of your approach. Then walk through each step of your plan and explain what it is doing. Be ure to highlight any challenges or inconsistencies that you see in the page along with any steps that I need to review.

Review the AI's proposed approach. Does it:

- Address the specific challenges of this dataset?
- Break down the process into clear steps?
- Consider edge cases or inconsistencies?
- Explain its reasoning for technical choices?

### Implementing the Extraction Code

Ask the AI to write the Python code and generate a CSV file of the data.

Review the code carefully, noting how it:

- Processes the HTML structure
- Identifies and extracts relevant fields
- Handles inconsistencies or errors
- Structures the resulting CSV

Copy the code your Jupyter Notebook and try to run it. Did it work or did it generate errors? See if you can fix your errors on your own (ex. you might need to adjust the file path of the HTML file or install requried libraries using `!pip install nameoflibrary`).

### Analyzing and Improving the Results

Open the outputted CSV file in Jupyter Lab. Are there any issues with the extracted data? Common problems might include:

- Missing data
- Incorrectly parsed fields
- Inconsistent formatting
- Merged or split records

Return to the AI with specific examples of problems and ask for improvements to the code:

> The extraction worked for some records, but I noticed these issues:<br> > [Describe specific examples of problems]<br>
> Rewrite the code to handle these issues.<br>

## Cleaning and Processing Data

### The Data

Let's use another webpage from the Frederick Bee Project: <https://www.frederickbee.com/habeasresidents.html>. This is described as: "Spreadsheet of the Habeas Corpus cases of the US District Court for the Northern District of California, San Francisco that lists the name of the Detained and the name of the Detained's father. For the period from October, 1889 to June, 1892.”

Note how this webpage is already formatted in a table. However, it's a table that's embedded in an HTML file. To make things easier, I just copy and pasted the table into a CSV file for you to use, which you can find in your `week-12` folder: `habeas-corpus-cases-1889-1892.csv` (or [download here]({{ "/modules/habeas-corpus-cases-1889-1892.csv" | relative_url }})) Open the CSV file in Jupyter Lab and take a look at its contents.

- What kind of information is contained in each of the columns?
- How is each column formatted?
- What are some issues you see with the way the data is recorded or stored?
- What are some ideas for historical questions you could ask using this data?

### Clean and Process the Data

Use ChatGPT to come up with a plan for how to clean the data. Before you start:

- To try and mitigate your usage limits, first generate a subset of the data: get a sample of 20 rows and write a new CSV file for this sample
- Start a new chat in ChatGPT and select `o4-mini-high` mode
- Spend some time crafting an opening prompt that asks it to come up with a plan for cleaning this data.
- Review its plan. What are the different steps? Which parts do you not understand?
- Ask it to generate code
- Try to implement the code on your full dataset
- Did it work? Did it miss any issues?

## Data Exploration

Now that we have our cleaned dataset, let's use Claude to help us explore and better understand the `habeas-corpus-cases-1889-1892.csv` data.

First, let's generate a sample of 25 rows from your cleaned dataset to make it easier to work with:

```python
import pandas as pd

# Load the cleaned dataset
df = pd.read_csv('cleaned_habeas_corpus_cases.csv')

# Select 25 random rows
sample_df = df.sample(n=25)

# Save the sample to a new CSV file
sample_df.to_csv('sample_habeas_corpus_cases.csv', index=False)
```

Now that we have our sample records, open Claude and start a new chat. Upload your sample CSV file and write a prompt to generate some ideas for how you might analyze the data.

- Provide it with historical context and detail about the dataset (see above)
- Ask it to explore and summarize some of the main features or patterns it sees in the data
- Ask it to generate ideas for specific research questions you could ask using this data
- Ask it for potential limitations or challenges with analyzing the data
- Note: some LLM's can be really "over-eager" and might start actually generating a bunch of code. This can rapidly hit your usage limit under the free plan. To mitigate this, include instructions in your prompt that explicitly tell it to not write any code that executes its research questions.

<!---
```
I'm working with historical data about habeas corpus cases filed for Chinese immigrants in the US District Court for the Northern District of California from 1889-1892. This data is from the Frederick Bee History Project, documenting the work of Frederick Bee who served as consul at the Chinese consulate in San Francisco and advocated for Chinese immigrants' civil rights during a period of extreme anti-Chinese sentiment.

Please examine this dataset and help me understand:
1. What patterns or trends do you notice in this data?
2. What are 5 specific questions I could investigate with this dataset?
3. What additional context or information might be useful to better understand these cases?
4. Are there any issues with the data that might affect analysis?
5. What fields or features in the data seem most significant for historical analysis?
```
--->

Review Claude's suggestions and identify which questions seem most interesting for further analysis.

## Data Analysis

Try implementing one of Claude's suggestions. Be sure to use the sample dataset and then try and implement its code for the full dataset in your Jupyter Notebook.

An example prompt:

> I want to analyze this dataset of historical habeas corpus cases for Chinese immigrants filed in San Francisco from 1889-1892. Please help me write Python code to count how many cases were filed each year and visualize the data. Make sure to: explain what the code is doing in comments and handle missing or inconsistent data appropriately.

Some other ideas for analysis you might want to try to implement with the help of your AI coding partner:

- How many women are in this dataset (noted by `(female)`)?
- How many detainees were held in prison (`Remand`) vs. allowed to go free (`Discharged`)
- Break the address column into three columns: `Address`, `City` and `State`. Note: if it doesn't have a city in the address, it's likely in San Francisco.
- What was age distribution of detainees? Note: if you didn't do so in Data Cleaning stage, you will need to reformat the `Age or year of birth` column to get this information.

<!--
```python
from bs4 import BeautifulSoup
import csv
import re

# Path to the HTML file
html_file = "/mnt/data/female-detainee-records.html"
# Output CSV path
csv_file = "/mnt/data/cases.csv"

# Read and parse the HTML
with open(html_file, 'r', encoding='utf-8') as f:
    soup = BeautifulSoup(f, 'html.parser')

# Prepare rows
rows = []
for a in soup.find_all('a'):
    href = a.get('href', '').strip()
    text = a.get_text(strip=True)

    # Extract case number and label
    match = re.match(r'Case\s*(\d+)\s*(.*)', text, re.IGNORECASE)
    if match:
        case_number = match.group(1)
        label = match.group(2)
    else:
        # Non-case links
        case_number = ''
        label = text

    rows.append({
        'case_number': case_number,
        'label': label,
        'href': href
    })

# Write to CSV
with open(csv_file, 'w', newline='', encoding='utf-8') as f:
    writer = csv.DictWriter(f, fieldnames=['case_number', 'label', 'href'])
    writer.writeheader()
    writer.writerows(rows)

print(f"CSV file written to {csv_file}")
```
-->
