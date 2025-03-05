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

The issue with a Jupyter Notebook file is that it can be tricky to show on a website. If you want to showcase your notebook on your Github Pages site, you can follow these steps:

- In Jupyter Lab, run all of the cells from start to finish so that they are outputting correctly
- In Jupyter Lab, go to `File` -> `Save and Export Notebook As` -> `HTML` then save the HTML file inside the `_pages` folder, naming it the same as your Jupyter Notebook file (substituting `.html` at the end for `.ipynb`)
  - This creates a "snapshot" of your Jupyter Notebook with all of its outputted cells, formatted as a static HTML file. If you double-click this file, you should see it opened up in web browser. This looks decent, but we're going to add some more code to make it make it show up as a page on your Github Pages portfolio site.
- Use Github Desktop to push your changes to your Github repository on Github.com
- Navigate to your `username.github.io` repository on Github.com
- Find your HTML file under the `_pages` folder. Click to edit the file and make changes.
- Copy and paste the following code at the very top of your HTML file and make sure to change the `title`, `permalink`, `date`, and `description` fields:

```yaml
---
layout: notebook
title: "Example Title You Can Change"
permalink: /some-file/
showcase: true
tools: ["Python"]
date: 2021-12-10
description: >
  This is an example of a Jupyter Notebook file rendered as a page on Github Pages.
---
```
