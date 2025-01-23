---
title: 💡 Coding Homework 01
toc: true
toc_sticky: true
classes: wide2
author_profile: false
---

## Overview

This assignment will help you get comfortable with the GitHub workflow we'll be using throughout the semester. You'll practice keeping your repository in sync, making changes both through GitHub.com and on your local computer, and maintaining good documentation habits.

## Review

- Before starting, make sure you've completed all the setup steps from the tutorial [💻 Getting Up and Running With GitHub]({{site.baseurl}}/modules/github-intro/):
  - Created a GitHub account
  - Installed GitHub Desktop
  - Forked the course repository and renamed it to include your last name (ex. `blevins-sp25-data-materials`)
  - Cloned your fork to your local computer

### Check For Updates

⚠️ ⚠️ ⚠️ Before starting any new work in this class, you always want to check for any updates from your instructor's `sp25-data-materials` repository.
{: .notice--warning}

- Open GitHub Desktop
- Make sure your course repository (`yourlastname-sp25-data-materials`) is selected
- Click `Fetch origin`
- Go to Branch → `Merge into current branch`
- Select "Other Branches" -> `upstream/main` from the list
- If there are no updates from the instructor, it will say "This branch is up to date with upstream/main"
- If there **ARE** updates from the instructor, it will say something like "This will merge 2 commits from upstream/main into main"
- If there are changes, click the button "Create a merge commit" to get any instructor updates
- If you click on History tab on the left, you'll see a summary of the new changes that have been made.
- If you open your folder on your computer, these local files will have been updated - but you have one remaining step: **you want to keep your local files up to date with your forked repository on Github.** Trust me - this will help you if you ever make some mistakes and need to "rewind" to recover files you might have accidentally deleted or changed.
- To keep them up to date, click the **"Push origin"** button in Github Desktop to sync these updates up to your GitHub fork
- Check to make sure the changes have been made - go to your repository in a browser on github.com (ex. https://github.com/YOURUSERNAME/yourlastname-sp25-data-materials) and see if the new files are there.

### Task 1: Add a New File and Push it to your Fork

- Inside your local `week-01` folder, navigate to `week-01-homework`
- Create a text file called `github-notes.txt` inside `week-01-homework`
- Write down EITHER the steps you followed to check for updates OR a question you have about the GitHub workflow
- Commit this file using GitHub Desktop with a descriptive summary
- Push the changes to your fork repository

### Task 2: Web-Based Editing on Github.com (with bonus Markdown practice!)

The next step is to create a new file on your fork on Github.com, then pull those updates down to your local computer. We are going to practice making a file in **Markdown** - a format we'll talk more about in coming weeks. Don't worry too much about it for now!

- Go to your repository on GitHub.com
- Navigate to your `week-01/week-01-hw` folder
- Create a new file called `about-me.md`
- This is a Markdown file. Take a look at the [Basic Syntax](https://www.markdownguide.org/basic-syntax/) guide and refer to it to do the following:
  - Write "About Me" as a Heading Level 1
  - Write "Goals for this class" formatted as Heading Level 2
  - Create a bulleted list of 2-3 things you hope to learn in this class
  - Use **bold** and _italics_ at least once each in your file
- Once you've finished, write a clear commit message describing what you added
- Commit the file directly on GitHub.com
- Look at the repository and click on the file - it should have a "preview" or your Markdown file that is properly formatted (with headings instead of `##` signs, etc.)
- Open GitHub Desktop and click "Fetch origin" to pull these changes to your computer

### Task 3: Adding a Local Image File

- Find a photo of one of your favorite places (can be a place you've been or want to visit)
- Save or move this photo to your `week-01/week-01-hw` folder on your computer
- Open GitHub Desktop and you should see the new file appear
- Write a descriptive commit message explaining what the photo is
- Push these changes to your repository

## Submission

Before submitting, check to make sure that your local copy and the fork on Github.com are matching up. They should have three new files in them:

- `github-notes.txt`
- `about-me.md`
- `some photo file`

- Submit the following on Canvas:
  - The URL to your GitHub repository (ex. https://github.com/yourusername/yourlastname-sp25-data-materials)
  - A screenshot of your local repository on your computer that shows all the above files inside the correct folder system
