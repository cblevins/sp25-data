---
title: Create a Project Repository on GitHub
---

## Overview

As part of your final [Research Project]({{ "/assignments/final-project" | relative_url }}), you are going to be creating a GitHub repositroy containing the code and data for your project. This is a valuable practice for a few reasons. First, it provides version control and a backup system, allowing you to track changes to your code and documents over time and revert or restore versions if you have computer failures or accidental deletions. Second, GitHub makes collaboration easier by allowing multiple researchers to work on the same project simultaneously. Although this is an individual project, you can see your instructor as a "collaborator" - this will allow them to more easily review and troubleshoot issues you might be having with your code or analysis. Finally, publishing your research project on GitHub makes your work accessible to others who might want to reproduce your findings or build upon your research.

## Create a New Repository on GitHub

1. Go to github.com and log in to your account
2. Click the "+" icon in the top-right corner and select "New repository"
3. Enter a name for your repository (`research-project`)
4. Add a description of your project and the context (ie. "Final Project for HIST 4261/5261: Working With Data, at CU Denver during the Spring 2025 semester")
5. Check the box to "Add a README file"
6. Click "Create repository"

## Clone the Repository to Your Computer

1. Open GitHub Desktop
2. Click on "File" → "Clone repository"
3. Select your newly created repository from the list of available repositories online
4. Choose where you want to save it on your computer - recommended inside your `working-with-data` folder
5. Click "Clone"

## Create Your First Commit

- Open Jupyter Lab on your computer
- Navigate to your local repository folder in Jupyter Lab
- Create a new Jupyter Notebook in your folder, something like `data-analysis.ipynb`
- Add a Markdown cell with your name and a very short description of your project
- Save your notebook

* Open GitHub Desktop
* You should see your changes listed in the left panel
* Enter a summary of your changes in the "Summary" field (e.g., "Add initial notebook")
* Click "Commit to main" to save your changes locally
* Click "Push origin" to upload your changes to GitHub

- Check the repository on Github.com to make sure that your changes have successfully been committed

## Document Your Project

- Edit the README.md file to include:
  - Your Name
  - Project title and description
  - Context for prooject (university, course, semester)

## Best Practices

- Commit your changes frequently to save your work and maintain version control
- Use meaningful file names
- Keep your data files organized and well-named
