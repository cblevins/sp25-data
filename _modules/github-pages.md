---
title: Introduction to GitHub Pages <i class="fa-brands fa-github"></i>
---

## Overview

Before diving into your portfolio website, you're going to create a simple practice site to learn the basics. We'll be using two key tools: GitHub Pages and Jekyll.

GitHub Pages is a free hosting service that takes files from your GitHub repository and turns them into a website. It's like a way to transform your code repository into a live website that anyone can visit. It's particularly useful for project documentation, personal blogs, and portfolios.

Jekyll is what's called a "static site generator" - it takes simple text files (written in Markdown) and converts them into a fully-functioning website. Instead of dealing with complicated HTML and CSS files, you can write your content in an easy-to-read format (Markdown), and Jekyll handles the hard work of creating a proper website structure. Jekyll is especially nice because it lets you use templates (called themes) to set your design and layout, so you can focus on your content.

In this tutorial, we'll create a basic Jekyll website and publish it using GitHub Pages. This will help you understand the fundamental concepts before we move on to creating your portfolio site. You'll learn how to:

- Set up a GitHub repository for web hosting
- Create basic website content using Markdown
- Use Jekyll to structure your site
- Monitor your site's deployment through GitHub Actions
- Make and preview changes to your live website

## Set Up Your Repository

The first step is going to be to create a new repository in your Github account that you will use to build an example website:

- Log into your GitHub account
- Click the "+" button in the top-right corner and select "New repository"
- Name your repository `example-site`
- Make sure the repository is set to "Public"
- Check the box that says "Add a README file"
- Click "Create repository"

## Create the Basic Jekyll Structure

- In your new repository, click "Add file" → "Create new file"
- Name it `_config.yml`
- Copy and paste the following code into the file. This is going to give your website a title, description, and load it with a visual theme (layout).

```yaml
title: My Example Site
description: Learning how to use Jekyll and GitHub Pages
remote_theme: pages-themes/minimal@v0.2.0
plugins:
  - jekyll-remote-theme # add this line to the plugins list if you already have one
```

## Add a Landing Page

- Click "Commit new file"
- Create another new file named `index.md`
- Copy and paste this code into the empty file:

```markdown
---
layout: home
---

# Welcome to My Site!

This is my first Jekyll site using GitHub Pages.

## About Me

Write a few sentences about yourself here.

## My Interests

- Interest 1
- Interest 2
- Interest 3
```

- Click "Commit new file"

## Enable GitHub Pages

You have content in here, but the last step to get a working website is to tell Github that you want to use this repository as a website - ie. you want to "build" the site based on the content you have in the repository.

- Go to your repository's Settings (click the gear icon)
- Click "Pages" in the left sidebar
- Under "Build and deployment":
  - Source: "Deploy from a branch"
  - Branch: select "main", keep "/(root)" as the folder
  - Click "Save"

## Check Your Site's Deployment

- Click on the "Actions" tab at the top of your repository
- You should see a workflow called "pages build and deployment" running
- The workflow will show:
  - Yellow dot = in progress
  - Green checkmark = successful deployment
  - Red X = failed deployment
- Click on the most recent workflow run to see details
- Under "deploy", you'll see the URL where your site is published. It should be: `https://yourusername.github.io/example-site`
- Once the workflow shows a green checkmark, your site is live! Go to `https://yourusername.github.io/example-site` and check!

## Understanding GitHub Pages Deployment

- Every time you commit changes to your repository:
  - GitHub Actions automatically starts a new "deployment"
  - Jekyll processes your markdown files into HTML
  - The built site is deployed to GitHub Pages
- You can see this process in real-time in the Actions tab
- The Actions tab helps you:
  - Confirm your changes are being deployed
  - Debug issues if something goes wrong
  - Find the exact time your changes went live

## Add A New Page

- In your repository, click "Add file" → "Create new file"
- Name the file `cat.md`
- Copy and paste the following content and then click "Commit new file":

```markdown
---
layout: page
title: My Cat
permalink: /cat/
---

Cats are so cool.
![](https://upload.wikimedia.org/wikipedia/commons/4/4f/A_domestic_pet_cat_inside_of_a_pet_stroller.jpg)
```

- Check the Actions tab, wait until the page has been successfully built and deployed, then reload your website
- Go to `https://yourusername.github.io/example-site/cat` and you should see the new page with a picture of your cat!

## Changing the Theme

You can easily change the theme of your Github Pages site to several "official" (or "supported") themes. These are fairly limited, but you can find a list here: <https://pages.github.com/themes/>.

- To change the theme, you'll need to update the `_config.yml` file
- Click `_config.yml` file in your repository then click on the pencil icon ✎ in the upper right to edit it.
- To change the theme, you'll replace the line of code that starts with `remote_theme`
- Let's try the [Dinky theme](https://pages-themes.github.io/dinky/) (lol) - replace the line of code with: `remote_theme: pages-themes/dinky@v0.2.0`.
- Your file should now look like this:

```yaml
title: My Example Site
description: Learning how to use Jekyll and GitHub Pages
remote_theme: pages-themes/dinky@v0.2.0
plugins:
  - jekyll-remote-theme # add this line to the plugins list if you already have one
```

- Check the Actions tab, wait until the page has been successfully built and deployed, then reload your website and see how the look and feel has changed (it will take a few minutes)
- Change your website to one of the following themes:

### Architect Theme ([Example](https://pages-themes.github.io/architect/))

```yaml
remote_theme: pages-themes/architect@v0.2.0
```

### Tactile Theme ([Example](https://pages-themes.github.io/tactile/))

```yaml
remote_theme: pages-themes/tactile@v0.2.0
```

### Hacker Theme ([Example](https://pages-themes.github.io/hacker/))

```yaml
remote_theme: remote_theme: pages-themes/hacker@v0.2.0
```

## Understanding Jekyll

- Jekyll is converting your `Markdown` files into `HTML` files (webpage files)
- The theme provides the overall design, look, and feel
- The `layout: page` in your about page tells Jekyll how to format an individual page
- The `permalink: /about/` creates a clean URL for the page

## Practice Exercises

Try these changes to explore how your site works:

- Add a new page called `projects.md`
- Add a link to our course website on you landing page using Markdown
- Add a new block of code on your site that contains a Python print statement

## Common Issues and Solutions

- If your site isn't appearing, check that:
  - Your repository is public
  - GitHub Pages is enabled on the main branch
  - You've waited a few minutes for changes to publish
- If your changes aren't showing up:
  - Make sure you committed them
  - Try clearing your browser cache
  - Wait a few more minutes
