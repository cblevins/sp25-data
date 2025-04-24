---
title: Organizing Your Research Project
---

## Overview

Your [Research Project]({{ "/assignments/final-project" | relative_url }}) requires you to conduct an extensive data-driven project. This will likely require you to work with a variety of different kinds of data, sources, files, etc. This tutorial will teach you best practices for keeping your research organized and making it available via GitHub.

## GitHub

You are going to be creating a GitHub repository containing the code and data for your project. This is a valuable practice for a few reasons. First, it provides version control and a backup system, allowing you to track changes to your code and documents over time and revert or restore versions if you have computer failures or accidental deletions. Second, GitHub makes collaboration easier by allowing multiple researchers to work on the same project simultaneously. Although this is an individual project, your instructor is a kind of "collaborator." Being able to review and troubleshoot issues is easier when you have your code available on Github. Finally, publishing your project on GitHub is part of a larger ethos of resaerch tranpsarency that makes your work accessible to others who might want to reproduce your findings or build upon your work.

### Create a New Repository on GitHub

We'll begin by creating a new empty repository on GitHub.

- Go to github.com and log in to your account
- Click the "+" icon in the top-right corner and select "New repository"
- Enter a name for your repository (`research-project`). Note: once you have finalized the topic of your project, you might want to change this to something that is more topical and specific to the subject matter.
- Add a description of your project and the context (ie. "Research Project for HIST 4261/5261: Working With Data, at CU Denver during the Spring 2025 semester")
- Check the box to "Add a README file"
- Click "Create repository"
- Under the newly created repository, edit the README.md file to add:
  - Your Name
  - Project title and description
  - Context for prooject (university, course, semester)
  - Commit your changes to the README.md file

### Clone the Repository to Your Computer

1. Open GitHub Desktop
2. Click on "File" → "Clone repository"
3. Select your newly created research project repository from the list of available repositories online
4. Under `Local Path` **Choose where you want to save it on your computer.** This is an important step as this is going to be the local folder you will be working in. I recommended putting it inside your `working-with-data` folder.
5. Click "Clone"

### Push your First Commit

- Open Jupyter Lab on your computer
- Navigate to your local repository folder in Jupyter Lab
- Create a new Jupyter Notebook in your folder, something like `data-analysis.ipynb`
- Add a Markdown cell with your name and a very short description of your project
- Save your notebook
- Open GitHub Desktop and make sure that your research project repository is selected under Current Repository
- You should see your changes listed in the left panel
- Enter a summary of your changes in the "Summary" field (e.g., "Add initial notebook")
- Click "Commit to main" to save your changes locally
- Click "Push origin" to upload your changes to GitHub
- Check the repository on Github.com to make sure that your changes have successfully been committed

## Organizing Your Research

Now that you have a repository for your research project, we're going to get your project workspace organized. Think of this as a more targeted refresher of your [Files and Folders]({{ "/modules/organizing-research" | relative_url }}) tutorial.

### Recommended Folder Structure

Given the scope of this project, it's important to make sure that all of your files and folders are organized logically. Moreover, to learn best practices for reproducible resaerch, we're going to make sure your work is oragnized in a way that doesn't just make it easier for _you_ to undersatnd, but makes it easier for _another_ person to understand. There's not a single "correct" way to approach this, but we are going to use the following folder structure within your repository.

In Jupyter Lab, use the navigation side bar to **create the following folder structure** inside your project repository folder. Note: you do NOT need to create the individual files - these are just examples of the kinds of files you might have inside each of the folders.

<!--
```
research-project/
├── README.md     # Overview of project and repository
├── notebooks/    # Folder for your Jupyter notebooks
│   ├── data-cleaning.ipynb     # notebook for data prep, processing, cleaning, etc.
│   ├── analysis.ipynb          # notebook for conducting initial analysis
│   └── visualizations.ipynb    # notebook for creating visualizations
│   └── data-essay-draft.ipynb  # notebook for writing a rough draft of project
│   └── data-essay-final.ipynb  # notebook for final version of research project
├── data/         # Folder of data files
│   ├── some-data.csv         # Original data source
│   └── other-data.xlsx       # Another original data source
│   └── some-data-cleaned.csv # Cleaned and processed version of original data source
├── output/       # Folder of figures or other things you generate with your code
│   └── bar-chart-01.png      # Data visualization image
│   └── map-01.html           # Interactive Folium map
├── assets/      # Folder of other material for your project
│   └── sources  # Folder of sources used during
│       └── some-primary-source.pdf   # Original source
│   └── img      # Folder of images
│       └── historical-photo-01.png   # Example of a historical image.
│       └── figure-01.png             # Image you want to use in your data essay
```
-->

**research-project/** - _Main project directory_

- **notebooks/** - _Folder for your Jupyter notebooks_
  - `data-cleaning.ipynb` - _Notebook for data prep, processing, cleaning, etc._
  - `analysis.ipynb` - _Notebook for conducting initial analysis_
  - `visualizations.ipynb` - _Notebook for creating visualizations_
  - `data-essay-draft.ipynb` - _Notebook for writing a rough draft of project_
  - `data-essay-final.ipynb` - _Notebook for final version of research project_
- **data/** - _Folder of data files_
  - **original/** - _Folder with original versions of datasets - never modify these_
    - `some-data.csv` - _Original data source_
    - `other-data.xlsx` - _Another original data source_
  - **processed/** - _Folder of datasets that you have actively processed, cleaned, etc._
    - `some-data-cleaned.csv` - _Cleaned and processed version data source_
- **output/** - _Folder of figures or other things you generate with your code_
  - `bar-chart-01.png` - _Data visualization image_
  - `map-01.html` - _Interactive Folium map_
- **assets/** - _Folder of other material for your project_
  - **sources/** - _Folder of sources used during research_
    - `some-primary-source.pdf` - _Original source_
  - **img/** - _Folder of images_
    - `historical-photo-01.png` - _Example of a historical image_
    - `figure-01.png` - _Image you want to use in your data essay_
- `README.md` - _Overview of project and repository_

### Understanding File Paths

When working with Jupyter notebooks, understanding file paths is essential:

- **Absolute paths** specify the complete location from the root of your file system (e.g something like: `C:\Users\YourName\Documents\research-project\data\processed\some-data.csv` on Windows or `/Users/YourName/Documents/research-project/data/processed/some-data.csv` on Mac/Linux)
- **Relative paths** specify location relative to the **current** working directory - typically the same directory as your Jupyter Notebook.
- When loading data in your notebooks, use relative paths - this will save you headaches and makes your code reusable for others:
  - If we take our above folder structure as a starting point, your "working directory" is the `notebooks` folder where you are storing your Jupyter Notebooks.
  - To access things in other folders you'll need to use relative file paths based on this directory. Some examples:
    - In a Python code cell: `pd.read_csv('../data/processed/some-data.csv')` means "go up **one** directory level (ie. `research-project` or whatever your repository folder is named), then go into the `data` folder, then open `some-data.csv`"
    - In a Markdown code cell: `![](../assets/img/historical-photo-01.png)` means "go up **one** directory level (ie. `research-project` or whatever your repository folder is named), then go into the `assets` folder, then go into the `img` folder, then insert the image file `historical-photo-01.png`"
