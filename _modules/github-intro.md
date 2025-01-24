---
title: Introduction to GitHub <i class="fa-brands fa-github"></i>
---

## Overview

As the name `Working With Data` implies, this class will involve a lot of hands-on work, either in class or on your own. It will require you to not only install different pieces of software, but to work with a lot of different kind of files (programming files, data files, etc.). In the module `Files and Folder`, you learned how to make and organize folders and files on your own computer. In this tutorial, we're going to learn about a different system of organization: Github<i class="fa-brands fa-github"></i> - one of the most widely-used platforms for sharing and collaborating on code and data projects.

At its core, GitHub is a way for people to work together on data-driven projects. It keeps track of changes to files over time (like an unlimited "undo" button), allows multiple people to work on the same project without overwriting each other's work, and makes it easy to share files with others. If you continue working with code or data after this class, you'll almost certainly encounter GitHub again - it's become an essential tool across many fields.

This guide will help you get set up with Github and the general workflow we're going to use in this class.

## The Github Repository System

Think of a GitHub `repository` (or "repo" for short) as a collection of files, folders, etc. You might create a repository to store all the files for, say, a research paper (storing your notes, drafts, data, and figures), a website you're building, or a programming project. To use a pen-and-paper analogy: it's like a three-ring binder with a bunch of papers and folders in it. But unlike a paper binder, a Github repository remembers every change you make to its contents - what changed, when it changed, and who changed it. It's like a super-powered version of Google Docs' revision history, but for any kind of file.

When you make changes to files in your repository - like editing a Python script or adding new data or even writing notes - you'll take a snapshot of those changes (called a `commit`). This creates a record that you can look back on or even return to if you need to undo something. Your repository also makes it easy to share your work with others. If you're working on a group project, your teammates can copy your repository to their own computers, make their own changes, and then sync everything back together. Or you might share it with your instructor when you need help debugging some code. Many people also use GitHub repositories to show off their work to potential employers - like a portfolio of your coding and data analysis skills.

## Using Github in this Course

For this course, you're going to be using several different Github repositories. We'll get into the other repository later in the semester, but the first repository consists of class material that you will use to complete weekly exercises, homework, tutorials, etc: `sp25-data-materials`. If you [take a look at the repository on Github.com](https://github.com/cblevins/sp25-data-materials), you'll see some folders for each week of the semester (`week-01`, `week-02`, etc.) along with files inside each folder.

Let's return to the three-ring-binder analogy: The instructor has a "main" binder (the `sp25-data-materials` repository) with course materials, all organized into different parts and sections. One solution would be for the instructor to photocopy all of the material in here and give each of you your own individual copy of the binder at the start of the semester. This system works fine if the binder never has to be changed. But what happens if your instructor wants to add new material or update existing material as the semester progresses? They'd need to make handouts and distribute them in class, and the students would have to hole-punch them, add them to the right section, etc. It would be a pain to keep everything up-to-date.

This is where Github comes in. A Github repository system gives you a way to **automatically** update your personal binder so that it matches the "main" instructor binder, all without touching your files and material that you've added to it. Any updates the instructor make are easily transferred over into your own repository without you needing to worry about organizing it all yourself. And if you are running into issues or confused about material, the instructor can also easily take a look at your binder to help troubleshoot and find a solution.

In our class, we'll be using a **three-level system** that enables everyone to work with the same core materials while maintaining their own personal workspace. Below is a diagram showing the relationship between these different levels:

![Image]({{ "/modules/img/git-flow-diagram.svg" | relative_url }})

- At the top level is the **instructor's repository** - think of this as the "main" copy of all course materials that lives on GitHub.com.
- When you create your own copy of this repository on GitHub.com (called "forking" the repository), you get the second level: **your personal Github fork**. This fork is like your own version of the course materials that also lives on GitHub.com, but is connected back to the instructor's repository so you can easily receive any updates.
- The third level is the copy of your fork that lives on your actual computer (created through a process called "cloning"). **This local copy** is where you'll do your actual work - creating new files, editing code, and analyzing data.
- When you make changes to files on your computer, you'll sync those changes back to your fork on GitHub.com. And when your instructor adds new material or makes updates to the original repository, you can easily pull those updates to your fork and to your local copy.
- This might sound complicated, but we're using a piece of software called GitHub Desktop to helps automate most of these steps - you mainly just need to remember to check for updates from the instructor's repository and regularly save your own work.

## Initial Setup

### Get Set Up

- If you have not done so already, follow [these instructions]({{site.baseurl}}/modules/installing-github/) to sign up for a Github account and install GitHub Desktop
- If you have not done so already in a previous tutorial, make sure you've created a course folder on your computer named `working-with-data` (I would recommend somewhere easy for you to navigate to and near the "root" of your computer - ex. in your "Documents" folder or something similar)
- Open GitHub Desktop and log in with your GitHub account

### Fork the Course Repository

- The first step is to "fork" the `sp25-data-materials` repository - this creates a duplicate copy of the instructor's repository of course materials within your own Github account.
- Make sure you're logged into GitHub
- Go to <https://github.com/cblevins/sp25-data-materials> in your web browser
- Click the "Fork" button in the top-right corner
- **Change the name of the repository** from `sp25-data-materials` to add your last name to the start of the repository name - ex. `blevins-sp25-data-materials`. This is not technically necessary, but will help future you keep the different repositories straight (ie. your instructor's and your own)
- Leave all other settings at their defaults and click "Create fork"
- Wait a moment while GitHub copies the repository to your account
- Go to your main user account page on GitHub: <https://github.com/yourusername>
- Click `Repositories` and you should see the new repository you just forked (copied) from the instructor. This is **your** version of the class material repository, living on GitHub's servers.

But you'll also want to also be able to work with this material on your own computer, not through a web browser on GithHub's servers. Which brings us to....

### Clone Your Fork Using GitHub Desktop

- To get your forked repostiroy onto your local computer, you are going to "clone" it
- Open GitHub Desktop
- Click "File" -> "Clone Repository"
- Select the tab Github.com
- Look for your forked repository (ex. `blevins-sp25-data-materials`) and select it from the list
- Under Local Path, navigate to your main course folder on your computer: `working-with-data`
- Click "Clone"
- Select "For my own purposes" in the dialog box
- If you go to `working-with-data` folder on your computer, you should see a new folder called something like `yourlastname-sp25-course-materials` (ex. `blevins-sp25-course-materials`). If you check inside it, you'll see a bunch of folders, each of which has some files and material already inside them. All of this should match your forked repository living on GitHub's servers.

## The Github Repository Workflow

Whenever you sit down to do any kind of coding work for this class (in class exercises, homework, assignments, etc.) you'll need to first see if the instructor has added any updates to the "main" repository of class materials. Follow these instructions to do so:

### Regular Updates (Do This Before You Start Anything New)

Before you start working each time, follow these four steps to make sure everything is up to date:

#### Step 1: Check for All Updates on Github.com (instructor repository & your forked repository)

- Open GitHub Desktop
- Make sure your course repository is selected
- Click `Fetch origin`

#### Step 2: Get Instructor Updates

- Go to Branch → `Merge into current branch`
- Select "Other Branches" -> `upstream/main` from the list
- If there are no updates from the instructor, it will say "This branch is up to date with upstream/main" - great! Continue to Step 3
- If there **ARE** updates from the instructor, it will say something like "This will merge 2 commits from upstream/main into main". Click `Create a merge commit`

#### Step 3: Get Any Changes from your personal repository on GitHub.com

- Click `Pull origin` if the button is available
- If the button is grey, you're already up to date!

#### Step 4: Final Sync

- Click `Push origin` to make sure your forked repository and your local copy are in sync

Now you're ready to work! Remember to repeat these steps each time you start working on course materials.

If you ever want to, here are instructions for updating your forked repository through Github's website (you'd then need to pull these changes down to your local copy on your computer):

- Go to your `yourlastname-sp25-data-materials` repository on Github.com
- Check and see if there have been any updates from the instructor. If there are, it will say something like `This branch is 1 commit behind cblevins/sp25-data-materials:main` at the top of the repository
- Note: if you make your own changes and additions to your own repository (which you will!) it will say `This branch is 1 (2, 3, 450, etc.) commits ahead of cblevins/sp25-data-materials:main` - that's okay!
- Click the "Sync fork" button near the top
- ⚠️ ⚠️ ⚠️ Do NOT click `Discard changes` - this will delete all of your own material, homework, etc. You _can_ undo this, but you'd rather not.
- Click "Update branch"
- Remember: this has only updated your **forked Github repository** that lives on Github's servers, NOT the local version **on your computer**. To make sure those updates get down to your computer, you'll need to open Github Desktop and click the `Fetch origin` button.

## Practice: Creating Your First File on GitHub.com

- We're going to practice adding a new file to this repository
- Click the "Add file" button near the top of the repository
- Select "Create new file"
- In the "Name your file" box, type: `week-01.txt`
- In the larger text box below, copy and paste: "This is some sample text for Week 1"
- Scroll to the bottom of the page
- Under commit new file:

  - In the first box, write a short message describing what you did (ex. "Added week-01.txt file")
  - Leave the "Add an optional extended description" box empty for now
  - Keep the "Commit directly to the main branch" option selected
  - Click the green "Commit new file" button

- Now your file is saved in your GitHub repository!
- Click on the file name to view it
- You can edit it by clicking the pencil icon (✏️) in the top right of the file view

## Practice: Making Your First Changes on your Computer

- First, let's create a simple text file using whatever program is available on your computer:

  - On Windows: Open Notepad (press Windows key and type "notepad")
  - On Mac: Open TextEdit (click the magnifying glass and type "textedit")
  - On either system: You can also use Word if that's what you're comfortable with

- Create a new file:

  - Type your name at the top of the file
  - Add today's date
  - Write "Figuring out how to use Github"
  - Save the file as `practice-notes.txt` in the `week-01` folder inside `yourlastname-sp25-data-materials` (the one you cloned to your computer)
  - Make sure to save it as a plain text file - if using Word, choose "Save As" and select "Plain Text (\*.txt)" as the file type

- Open GitHub Desktop and you should see your new file appearing in the "Changes" tab

  - The left panel will show your new file in green (indicating it's been added)
  - The right panel will show the contents of your file in green

- Create your first commit

  - At the bottom left of GitHub Desktop, write a brief "Summary" of what you did (ex. "Added practice notes file")
  - Click "Commit to main"
  - Click "Push origin" to sync these changes to your GitHub fork

- Verify your changes online
  - Go to your repository on GitHub.com - ex. `https://github.com/yourusername/yourlastname-sp25-data-materials`
  - You should see your new `practice-notes.txt` file
  - Click on it to make sure the contents are there

## Practice: Getting Updates from your Instructor's Repository

Let's practice getting updates from the instructor's repository in real time.

First, make sure your repository is up to date before we start:

- Open GitHub Desktop
- Click "Fetch origin"
- If you see "Pull origin", click that too
- Go to Branch → "Merge into current branch"
- Select "upstream/main"
- If it says "This branch is up to date with upstream/main", you're ready!

Your instructor will now make some changes to the `week-01` folder in the main course repository

- Watch what they're doing - they might add a new file or modify an existing one
- This simulates how new course materials will be added throughout the semester

Once the instructor has made their changes, let's get those updates:

- In GitHub Desktop, click "Fetch origin"
- Go to Branch → "Merge into current branch"
- Select "upstream/main" again
- This time, you should see a message about new changes to merge
- Click "Create a merge commit"

Let's verify the updates worked:

- Look in your local `week-01` folder - you should see the new or modified files
- In GitHub Desktop, click the "History" tab on the left
- You should see the instructor's recent changes listed there
- Click on the commit to see exactly what changed (green shows additions, red shows deletions)

Final step - keep everything in sync:

- Click "Push origin" to sync these updates to your GitHub fork
- Go to your repository on GitHub.com to verify the changes are there
