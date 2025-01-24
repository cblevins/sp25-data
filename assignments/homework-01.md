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

- Before starting, make sure you've completed all of the following steps from the tutorial [💻 Getting Up and Running With GitHub]({{site.baseurl}}/modules/github-intro/):
  - Created a GitHub account
  - Installed GitHub Desktop
  - Forked the course repository and renamed it to include your last name (ex. `blevins-sp25-data-materials`)
  - Cloned your fork to your local computer

As a reminder, here is the GitHub workflow:

![Image]({{ "/modules/img/git-flow-diagram.svg" | relative_url }})

### Check For Updates

⚠️ ⚠️ ⚠️ Before starting any new work in this class, you always want to check for any updates from your instructor's `sp25-data-materials` repository.
{: .notice--warning}

- Open GitHub Desktop and select your course repository
- Click `Fetch origin` to check for any changes
- Go to Branch → `Merge into current branch` → select `upstream/main` and click `Create a merge commit` if there are updates
- Click `Pull origin` if it's available (if not, you're up to date!)
- Click `Push origin` to sync everything up

### Task 1: Add a New File and Push it to your Fork

- Inside your local `week-01` folder, navigate to `week-01-homework`
- Create a text file called `github-notes.txt` inside `week-01-homework`
- Write down either a question you have about the GitHub workflow OR which Github vocabulary word you find the funniest: fork, clone, or fetch.
- `Commit` this file using GitHub Desktop (ie. officially take a snapshot of your changes)
- Push the changes to your fork repository

### Task 2: Web-Based Editing on Github.com (with bonus Markdown practice!)

The next step is to create a new file on your fork on Github.com, then pull those updates down to your local computer. We are going to practice making a file in **Markdown** - a format we'll talk more about in coming weeks. Don't worry too much about it for now!

- Go to your repository on GitHub.com
- Navigate to your `week-01/week-01-homework` folder
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
- Save or move this photo to your `week-01/week-01-homework` folder on your computer
- Open GitHub Desktop and you should see the new file appear
- `Commit` these changes with a summary message explaining what the photo is
- `Push` these changes in Github Desktop to your forked repository on Github.com

## Submission

Before submitting, check to make sure that your local repository and your forked repository on Github.com are matching up. Each of them should have three new files in `week-01-homework` folder:

- `github-notes.txt`
- `about-me.md`
- `some photo file`

- Submit the following on Canvas:
  - The URL to your GitHub repository (ie. https://github.com/yourusername/yourlastname-sp25-data-materials)
  - A screenshot of your local repository on your computer that shows all the above files inside the correct folder system (Screenshot instructions for [Mac](https://support.apple.com/guide/mac-help/take-a-screenshot-mh26782/mac#:~:text=Press%20Shift%2DCommand%2D3.&text=Press%20Shift%2DCommand%2D4%2C,the%20mouse%20or%20trackpad%20button.&text=Press%20Shift%2DCommand%2D4%2C%20then%20press%20the%20Space%20bar.), [Windows](https://support.microsoft.com/en-us/windows/use-snipping-tool-to-capture-screenshots-00246869-1843-655f-f220-97299b865f6b))
