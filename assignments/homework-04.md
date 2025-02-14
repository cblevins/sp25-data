---
title: Homework 04
toc: true
toc_sticky: true
classes: wide2
author_profile: false
---

## Overview

This assignment will help you finish getting your portfolio website up and running.

## Tutorial Checklist

You are going to follow the instructions to finish all the steps in the tutorial [💻 Building a Portfolio Site with Github Pages]({{site.baseurl}}/modules/portfolio-site). Here is a checklist of everything you need to do in that portfolio (note: you did many of these in class):

- [ ] Fork and rename the template repository to `yourusername-sp25-data-portfolio`
- [ ] Update repository URL settings in `_config.yml` (`url` and `baseurl` variables)
- [ ] Make sure the Github Pages settings are updated so that it is building and deploying the site
- [ ] Personalize site details in `_config.yml` (`title`, `name`, `email`, `description`)
- [ ] Update social links in `_config.yml` (GitHub URL and optional LinkedIn)
- [ ] Edit homepage content in `index.md` with a personal introductory sentence.
- [ ] Add a new profile picture image to `/assets/img/` folder
- [ ] Update the `profile_image` path in `index.md` front matter to point to your new image file
- [ ] Update project review page date in `project-review.md`
- [ ] Add placeholder content to `project-review.md`
- [ ] Modify the navigation menu in `_config.yml` to include link to Project Review page
- [ ] Verify site is live at `https://yourusername.github.io`

## Idea for Project Review

Instead of emailing your instructor an idea for the [🔍 Project Review]({{site.baseurl}}/assignments/project-review), you're going to write your idea in your Project Review page. Add 1-2 sentences to the main content of the `project-review.md` file that shares what project you are thinking of reviewing. Use Markdown to [add a URL link](https://www.codecademy.com/resources/docs/markdown/links) to the project itself.

## Insert an Image

To get you ready for your Project Review, you're going to practice inserting an **image** into a page (which you'll need to do for the assignment). In particular, you'll probably want to use a screenshot to illustrate some of your analysis.

- Take a screenshot of this page (ie. this homework page on our course website).
  - [Instructions for Mac](https://support.apple.com/en-us/102646)
  - [Instructions for Windows](https://support.microsoft.com/en-us/windows/use-snipping-tool-to-capture-screenshots-00246869-1843-655f-f220-97299b865f6b)
- Save and/or then locate the file on your computer.
- Take a look at the file name. It likely ends in `.png` (the type of image file that most systems use for screenshots). Whatever the file ending is (`.png`, `.jpg`, etc.), change the rest of the file name to `example-screenshot` so that your file is now named `example-screenshot.png` (or `example-screenshot.jpg`, etc.)
- On Github, navigate to `assets` -> `img` folder and then add the screenshot file to that folder (follow same instructions as you did in the tutorial for the profile picture)
- Check and make sure you now have another file called `example-screenshot.png` (or `example-screenshot.jpg`, etc.) in the `img` folder
- Open `project-review.md`
- At the bottom of the file, copy and paste the following code - note: if you named the image something else, you'll need to update that part of the code with the correct file name (ex. replacing `.png` with `.jpg`)

```html
<div align="center">
  <p><img src="/assets/img/example-screenshot.png" style="width: 80%;" /></p>
</div>
```

- Once the site has been built and deployed, check your Project Review page (go to `https://yourusername.github.io/project-review/`) and make sure that the screenshot has been inserted correctly.
- This code snippet you inserted is written in HTML. It does the following:
  - Make a block of content on your page and center it
  - Adds the image you just uploaded (pointing it towards the correct location in `assets` -> `img` folder)
  - Displays the image at 80% of the width of the page
- You can reuse this code for your Project Review assignment, adjusting it to point towards the actual images you want to use.

## Optional Bonus Tasks for your Portfolio Site

- Add a brand new page to the site called "Skills". Make a list of either your existing technical skills or ones you hope to learn in this class. Add a link to the site's navigation bar that allows a user to navigate to this new page.
- The theme we're using is able to display a variety of social media icons at the bottom of the site (the footer). [Here is a list](https://fontawesome.com/search?o=r&ip=brands) of all of them. See if you can figure out how to add an additional icon that's not already in the `_config.yml` file. Note: you can just use a fake URL if you don't want to link to a personal social media account.

## Submission

Submit a link to your portfolio homepage on Canvas.
