---
title: Building a Portfolio Site with Github Pages
---

## Overview

You'll be converting a template repository into your own personal website hosted on GitHub Pages. This site is going to be where you complete your major assignments, with the goal of having a portfolio of your work at the end of the semester. By the end of this module, you'll have a live website at `https://yourusername.github.io` that you can further customize with your own content.

## Fork and Rename the Repository

The first step is to "fork" a template that your instructor created for you. This will serve as your starting point that you will modify and adjust to make it your own portfolio site.

- Go to the [template repository](https://github.com/cblevins/sp25-data-portfolio) on GitHub.
- Click the "Fork" button in the upper right corner.
- Rename the repository `yourusername.github.io` (replace 'yourusername' with your actual GitHub username - ex. `cblevins.github.io`).
- Click Create Fork

## Change the site's URL

- Under your repository on Github (ex. `https://github.com/yourusername/yourusername.github.io/`) you'll see a number of folders and files. You don't need to worry about understanding them all.
- The first file you want to edit to start personalizing the site is `_config.yml`. This is kind of like the command center of your site and where you configure your site's title, URL, site-wide settings, etc.
- Open the `_config.yml` file in your repository on Github.com and click the pencil icon to edit the file
- Notice that `_config.yml` uses **variables** just like Python - it is storing values inside the names of things like `title`, `author` or `description`. Changing the values of these variables in this file will then change different aspects of the site.
- Look for the two lines of code starting with `url` and `baseurl`. Changes them to these two lines of code (substituting your Github username)

```yaml
url: "https://yourusername.github.io" #Your Github username
baseurl: "" # Remove the baseurl content since this will be your main site
```

- Commit your changes.

## Enable GitHub Pages

- On your repository's page on Github.com, click Settings
- Scroll down to the "GitHub Pages" section
- Under "Source", select `main`
- Click "Save"
- Go to the Actions tab and wait a few minutes until you see a green checkmark next to pages-build-deployment.
- Open up `https://yourusername.github.io` in a new tab and see if it's working!

## Personalize the Site

- Return to `_config.yml` and take a look at some of the variables. Try and find their values on the rendered website (`https://yourusername.github.io`) to figure out which lines of code are changing which portions of the webpage.
  - For example, the text contents of the `description` variable are getting displayed at the bottom (footer) of the website.
- Change the following variables to personalize the site for you:
  - `title`
  - `name`
  - `email`
  - `description`
  - Under `social_links` -> change the Github `url` to your Github url. Optional: change the LinkedIn URL to your LinkedIn Page.

## Working With Pages

The `_pages` folder in a Jekyll site is where you store standalone pages for your website - the key pages that structure your site's navigation and content. Let's practice editing pages by customizing two important files: your homepage (`index.md`) and your project review page (`project-review.md`).

### Front Matter

"Front matter" (or "YAML") is a chunk of text at the beginning of any page, set between sets of triple dashes (`---`). It contains information about that particular page and tells Jekyll how to process and display it.

- Open the file `index.md` under the `_pages` folder and click the button that says `Raw`
- You should see front matter that looks like:

```yaml
---
layout: home
title: About Me
permalink: /
profile_image: /assets/img/profile.jpg # Add your image path here
---
```

- These are variables that are telling Jekyll certain things about the page - ex. `layout` variable determines how the page should be formatted, while the `profile_image` points Jekyll towards the image file to use on the landing page (currently Albert Einstein - you'll change this eventually)

### Edit Your Homepage (index.md)

- Beneath the YAML front matter is the actual **content** of your landing page.
- Expand it to include some more personalized touches. For instance, you might write:

```
I'm [Your Name], a student at [Your University] studying [Your Field]. This portfolio showcases my work in HIST 4261/5261: Working With Data.
```

### Change Your Profile Picture (index.md)

- Let's change the current profile photo that is defined in the YAML front matter:
- Navigate to `assets` -> `img` within the Code section nof the Github repository and locate the `profile.jpg` file.
- Let's add a second image file to this `img` folder that we're going ot use intsead for your profile. If you have a photo of yourself you want to add, upload it here nad name it `profile-1` (with whatever file type ending after it - ex. `profile-1.jpg` or `profile-1.png`)
- If you don't have a photo of yourself you want to use, let's add a temporary placeholder image of the CU Denver logo. Download the logo from [this page](https://www.ucdenver.edu/images/default-source/global-theme-images/cu_logo.png), then upload the file into the `img` folder and rename it `profile-1.png`
- Change the YAML front matter in `index.md` to change where it says `profile.jpg` to say `profile-1.png` (or .jpg or whatever file you chose)
- Once Github has fininshed building and deploying your site, see if the image is updated!

### Edit Your Project Review Page (project-review.md)

- The page `project-review.md` (in the `_pages` folder) is an empty placeholder file. You will edit this file to complete and submit your first major assignment of the semester (your project review).
- Look at the front matter and note the variable `date`.
- If you look below the front matter at the content, you will see some text that is referencing the variable `date` defined in the front matter (it's doing so via some curly brackets surrounding `page.date`). Go to `https://yourusername.github.io/project-review` - notice how it's printing the _value_ of that variable.
- Try changing the value of `date` to today's date.
- Edit the content of the page (beneath the front matter) by adding the words "this is some more placeholder text" on a new line.
- Commit your changes
- Go to your repository's Actions tab, wait until it has finished deploying, then go to `https://yourusername.github.io/project-review` and see if your changes are getting rendered correctly.

## Site Layout and Navigation

You'll want to make sure your site is easy and logical to navigate for a user. The main way they will do this is through the navigation links on the top of the page. To make modifications to these you'll change this part of the `_config.yml` file:

```yaml
navigation:
  main:
    - title: "About Me"
      url: "/"
    - title: "Portfolio"
      url: "/portfolio/"
    - title: "Another Website"
      url: "https://cblevins.github.io/sp25-data/"
```

- Notice how each link has two variables: the `title` which is the text you want to show up on the top of your website that a user can click on, and the `url` which is a link to the actual page you want them to be able to navigate to
- The last navigation link shows you how you can add a link to somewhere else (not just a page on your portfolio site). We don't actually need this.
- To practice adding a new link, replace the last two lines of code with a link to your Project Review page:

```yaml
- title: "Project Review"
  url: "/project-review/"
```

- This is just a temporary link that will allow your instructor to easily navigate to that page. Later in the semester we'll get rid of it

## Troubleshooting

If you encounter issues:

- Verify that your repository name exactly matches your username followed by `.github.io`
- Check that GitHub Pages is enabled in your repository settings
- Look in the "Actions" tab for any build errors
- Ensure all changes to `_config.yml` maintain proper YAML formatting (spacing is important)
