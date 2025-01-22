---
title: Files and Folders
---

### Files and Folders on your Computer

Your computer has a system of folders (directories) that contain individual files. For the rest of the semester, you are going to store all files and material related to this class under a single course folder on your computer. Here are some resources for navigating files and folders on your computer:

- Mac:
  - [Get to know Finder on your Mac](https://support.apple.com/en-us/HT201732)
  - [Organize files in folders on Mac](https://support.apple.com/guide/mac-help/organize-files-with-folders-mh26885/)
- Windows:
  - [How to get to the Desktop, Documents, and Pictures folders in File Explorer](https://support.microsoft.com/en-us/windows/how-to-get-to-the-desktop-documents-and-pictures-folders-in-file-explorer-3370f06b-0f8d-4b25-be9a-3ee54f381e3d)
  - [Create a New Folder in Windows](https://support.microsoft.com/en-us/office/create-a-new-folder-cbbfb6f5-59dd-4e5d-95f6-a12577952e17#:~:text=the%20new%20folder.-,Create%20a%20new%20folder%20before%20you%20save%20your%20document%20by%20using%20File%20Explorer,-Open%20File%20Explorer)

### Making a Course Folder on your Computer

Go ahead and make a **new folder on your computer called `working-with-data`**. I would recommend choosing a location on your computer that is fairly easy to navigate to and find. For instance, both Windows and Mac come with an existing `Documents` directory. If you navigate to this folder you can then create a folder inside `Documents` named `working-with-data`. Your `working-with-data` is going to be your "parent" folder moving forward for this class. Any work you do, make sure that it is saved under this folder.

### Organizing Your Files and Folders

Now that you've created your course folder, let's practice creating and organizing a more complex set of folders and files:

- Create a new folder inside `working-with-data` called `my-photos`
- Inside `my-photos`, create two more folders:
  - `animals` (for animal photos)
  - `landscapes` (for nature/landscape photos)
- Download these practice images and save them in the correct folders:
  - [racoon.jpeg]({{site.baseurl}}/modules/img/racoon.jpeg) → save in the `animals` folder
  - [gs104.jpg]({{site.baseurl}}/modules/img/gs104.jpg) → save in the `landscapes` folder
  - [sunset 1.jpg]({{site.baseurl}}/modules/img/sunset 1.jpg) → save in the `landscapes` folder
- Your folder structure should now look like this:

```
working-with-data
    my-photos
        animals
            racoon.jpeg
        landscapes
            gs104.jpg
            sunset 1.jpg
```

### Naming Files and Folders

Having the right names for your files and folders is surprisingly important! Here are some key rules to follow:

- **Never use spaces** in file or folder names - use hyphens (`-`) or underscores (`_`) instead
- Use descriptive names that tell you what the file or folder contains
- Keep names short but meaningful
- Use all lowercase letters

Looking at your `landscapes` folder, you have two files with problematic names:

- `gs104.jpg` - this name isn't descriptive
- `sunset beach.jpg` - this name contains a space

To see the issue with spaces in filenames, click on the [original link]({{site.baseurl}}/modules/img/sunset 1.jpg) I gave you to download the image `sunset 1.jpg`. Take a look at the URL in your browser - it should end in `sunset%201.jpg` NOT `sunset 1.jpg`. The weird text in the middle is a result of the space in the filename and can throw things off if you were trying to actually work with this file computationally. Instead of spaces, I would recommend using hyphens (`-`)

Let's fix these on your computer! Rename both files to follow correct naming conventions:

- Rename `gs104.jpg` to `mountains.jpg`
- Rename `sunset 1.jpg` to `beach-sunset.jpg`

Your folder structure should now look like this:

```
working-with-data
    my-photos
        animals
            racoon.jpeg
        landscapes
            mountains.jpg
            beach-sunset.jpg
```

These might seem like small changes, but clear naming will become crucial as you work with more complex files throughout the semester. Good naming helps you:

- Find files quickly
- Know what's in a file without having to open it
- Share files with others
- Avoid technical problems that can arise from spaces or special characters in filenames

<sl-alert variant="warning" open>
  <sl-icon slot="icon" name="exclamation-triangle"></sl-icon>
  <strong>Too easy?</strong><br />
  Experiment with trying to rename some of your image files or folders only using the command line (<a href="https://melaniewalsh.github.io/Intro-Cultural-Analytics/01-Command-Line/01-The-Command-Line.html">instructions</a>)
</sl-alert>
