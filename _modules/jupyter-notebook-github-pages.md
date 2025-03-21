---
title: Working With Jupyter Notebooks and Github Pages
---

These instructions will help you work with Jupyter Notebooks and process them so that they display on your Github Pages portfolio site.

## Github Pages

- Make sure you have a local version on your computer of your Github Pages portfolio site repository.
- Open Github Desktop then go to `File` -> `Clone Repository...`
  - Under `Your Repositories`, select the repository for your Github Pages portfolio site - it should say something like `yourusername/yourusername.github.io`.
  - Under `Local Path` select `Choose...` and navigate to the folder on your computer `working-with-data` then add a new folder that matches the name of your repository on Github: `yourusername.github.io`
- Select `For my own purposes` in the dialog box

## Jupyter Lab & Jupyter Notebook

- Use Anaconda Navigator to open Jupyter Labs, then navigate to the local folder `yourusername.github.io` and the subfolder `pages`
- Create a new Jupyter Notebook file.
- Rename and save the file, making sure it is saved under the `_pages` subfolder
- Your first cell should be a Markdown file that includes a title for your notebook (using a header - `#` or `##`)

## Using Images in Jupyter Notebook

There are a few different ways to include images in a Jupyter Notebook.

- The first step is to have a local copy of the image file inside your repository. Make sure that you **don't have any spaces in the filename** and move the image file into the subfolder: `yourusername.github.io` -> `assets`-> `img`
- If you want to be able to format the image and its appearance, you can use HTML code inside a Markdown cell. The following code will do the following:
  - Center the image
  - Locates the file to insert it
  - Makes it smaller (60% the size of the original)
  - Adds a border line around the image
  - Adds "alt text" - a description of the image for vision impaired readers
  - Adds a formatted caption under the image

```html
<div align="center">
  <img
    src="../assets/img/profile-1.png"
    width="60%"
    style="border: 2px solid"
    alt="Description of image"
  />
  <figcaption style="font-style: italic">
    Detailed description of what the image represents
  </figcaption>
</div>
```

- If you **don't** want to format the image at all (ex. resize it, center it, etc.) you can insert it very easily using the following Markdown syntax:

```
![](../assets/img/yourimagefile.jpg)
```

## Rendering a Jupyter Notebook on Github Pages

The issue with a Jupyter Notebook file is that it can be a bit tricky to display on a website. If you want to showcase your notebook on your Github Pages site, follow these steps:

- In Jupyter Lab, run all of the cells in your notebook from start to finish so that they are outputting correctly.
- In Jupyter Lab, go to `File` -> `Save and Export Notebook As` -> `HTML` then save the HTML file inside the `_pages` folder, naming it the same as your Jupyter Notebook file (substituting `.html` at the end for `.ipynb`)
  - This creates a "snapshot" of your Jupyter Notebook with all of its outputted cells, formatted as a static HTML file. If you double-click this file on your computer and open it in a web browser, you should see the cells and their output. This looks decent, but we're going to add some more code to integrate the file as a page on your Github Pages portfolio site.
- Use Github Desktop to write a commit message, click `Commit to main` and then `Push origin` to get the changes from your local repository to your Github repository on Github.com
- Navigate to your `username.github.io` repository on Github.com
- Locate the newly created HTML file from your notebook under the `_pages` folder. Click the pencil icon to edit the file.
- Copy and paste the following YAML frontmatter at the very top of your HTML file.

```yaml
---
layout: notebook
title: "Example Title You Will Change"
permalink: /some-notebook/
showcase: true
tools: ["Python"]
date: 2025-01-01
description: >
  This is an example of a Jupyter Notebook file rendered as a page on Github Pages.
---
```

- ⚠️ Make sure to change the values for the `title`, `permalink` (change to something specific for your notebook), `date`, and `description` variables. In particular, the `permalink` variable will determine for your notebook page - ie. `/some-notebook/` will create the URL: `yourusername.github.io/some-notebook/`.
- When you commit your changes, wait for Github Pages to build and deploy your site then check to see if the page is appearing correctly by going to `https://username.github.io/` + whatever you edited the `permalink` to in its frontmatter - ie. `https://username.github.io/some-notebook/`.

## Updating Your Notebook on Github Pages

The annoying part of this workflow is that if you want to update or change anything on your page you will need to redo the last several steps by hand (ie. updating the HTML file and adding the YAML frontmatter). Follow these instructions for making changes:

- In Github Desktop: click `Fetch Origin` then `Pull origin` to get changes from your Github repository
- Open your Jupyter Notebook file in Jupyter Labs and make any necessary changes, then re-run all the cells and make sure they're outputting everything properly.
- Export an updated HTML file into your `_pages` folder but **name it something different**. You can add `-temporary` to the end of it (ex. `some-notebook-temporary.html`). You should now have two HTML files in the `_pages` folder.
- Use Github Desktop to write a commit message, click `Commit to main` and then `Push origin` to get the changes from your local repository to your Github repository on Github.com
- Open your repository on Github.com, navigate to the `_pages` folder and make sure you now have two HTML files (ie. `some-notebook.html` and `some-notebook-temporary.html`).
- Click the newer HTML file you just created (ex. `some-notebook-temporary.html`) and click the copy icon <i class="fa-solid fa-copy"></i> to copy the entire contents of the fil
- Open the older HTML file (ex. `some-notebook.html`), click the pencil icon <i class="fa-solid fa-copy"></i> to edit it:
  - Delete everything BENEATH the YAML frontmatter - ie. keep everything from `---` to `---` but delete everything else.
  - A keyboard shortcut to select all of this code without needing to select and scroll with your mouse is to click so your cursor is at the very beginning of the text you want to delete then:
    - Mac: `SHIFT` + `CMD` + `Down arrow ⬇️`
    - Windows: `Ctrl` + `Shift` + `End`
  - Paste the YAML frontmatter you copied into the very beginning of the document
  - Commit your changes to save and update the file
- I would recommend deleting the temporary HTML file since you don't need it anymore:
  - Open the file on Github.com (ex. `some-notebook-temporary.html`)
  - Click the button with the three dots in the upper right then choose -> `Delete file` and
  - Click green `Commit changes` button
- Open Github Desktop click `Fetch Origin` then `Pull origin` to update your local folder to reflect these changes
