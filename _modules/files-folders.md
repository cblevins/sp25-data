---
title: Files and Folders
---

### Files and Folders on your Computer

Your computer has a system of folders (directories) that contain individual files. For the rest of the semester, you are going to store all files and material related to this class in a new folder on your computer. Here are some resources for navigating files and folders on your computer:

- Mac: 
	- [Get to know Finder on your Mac](https://support.apple.com/en-us/HT201732) 
	- [Organize files in folders on Mac](https://support.apple.com/guide/mac-help/organize-files-with-folders-mh26885/)
- Windows: 
	- [How to get to the Desktop, Documents, and Pictures folders in File Explorer](https://support.microsoft.com/en-us/windows/how-to-get-to-the-desktop-documents-and-pictures-folders-in-file-explorer-3370f06b-0f8d-4b25-be9a-3ee54f381e3d) 
	- [Create a New Folder in Windows](https://support.microsoft.com/en-us/office/create-a-new-folder-cbbfb6f5-59dd-4e5d-95f6-a12577952e17#:~:text=the%20new%20folder.-,Create%20a%20new%20folder%20before%20you%20save%20your%20document%20by%20using%20File%20Explorer,-Open%20File%20Explorer)

### Making a Course Folder on your Computer

Go ahead and make a **new folder on your computer called `intro-digital-studies`**. It is up to you where you want this folder to be located on your computer. If you already have an organization system for course and schoolwork, feel free to continue using it. If you do **not** have a file organization system, I would recommend choosing a location on your computer that is fairly easy to navigate to and find. For instance, both Windows and Mac come with an existing `Documents` directory. If you navigate to this folder you can then create a folder inside `Documents` named `intro-digital-studies`.

Your `intro-digital-studies` is going to be your "parent" folder moving forward for this class. I would recommend making sub-folders within that folder to help organize your files: make at least an `assignments` folder and a `tutorials` folder.

Open up the `tutorials` folder and make, **make a new folder for this tutorial called `files-folders`**. Open [this photo of Professor Blevins's cat]({{site.baseurl}}/modules/prof-blevins-cat.jpeg) and right click the image to save it to your computer inside the new `files-folders` folder you just created (leave the name as `prof-blevins-cat.jpeg`). 

Your folder struture on your computer should look something like this:

```
intro-digital-studies
	assignments
	tutorials
		files-folders
			prof-blevins-cat.jpeg
```

### Files and Folders on Reclaim Hosting

Just like your computer has a system of files and folders, your Reclaim Hosting account comes with a system of files and folders that exist remotely, on their servers. You can find and work with these folders through Reclaim Hosting's `File Manager` tool. 

- [Log in to your Reclaim Hosting account](https://portal.reclaimhosting.com/clientarea.php) 
- Click on `cPanel`. This is the overview page where you can manage a bunch of different aspects of your account with Reclaim Hosting (such as URL domain names, setting up an email account based on your domain, etc.). 
- Find `File Manager`and open it in a new browser tab, which will bring you to an interface showing you some folders. Much like your physical computer, your server space at Reclaim Hosting is organized into a collection of folders containing files, scripts, folders, etc. Don't worry about what all of them mean. 
- For now, navigate to the folder `public_html`. The `public_html` folder contains stuff that you want to be accessible by other people through an internet browser. 
- Anything you put inside the `public_html`  is going to be publicly accessible to anyone with your domain URL (unless you password protect it).
- When you start adding sub-folders or material within your `public_html` folder they can be accessed by appendeding the folder names to that URL. So if your `File Manager` structure looks like:

```
public_html
	some-folder
		some-file.jpeg
```

- Then someone can access the file `some-file.jpeg` by going to the URL: `https://yourdomainnameurl/some-folder/some-file.jpeg` (ex. `https://janedoe.reclaim.hosting/some-folder/some-file.jpeg`).  

### Make a Sandbox Directory on Reclaim Hosting

Your first step is to make a "sandbox" folder inside your `public_html` directory. This is where you can mess around and try things out without worrying about anything breaking. To create your sandbox folder:

- Make sure you are in File Manager in Reclaim Hosting (Reclaim Hosting Dashboard -> cPanel -> File Manager)
- Navigate to the `public_html` folder and make sure you are inside that folder
- Add a new folder within your `public_html` folder called `sandbox` (make sure it says `public_html` under "New folder will be created in:")
- Navigate to the folder. It should be empty. :smile:

### Upload a file to File Manager

Because it is inside the `public_html` main folder, anything inside the `sandbox` folder can be accessed by somebody from their browser through your domain URL. Let's add a file into it and see if someone can download it:

- Navigate in File Manager to your `sandbox` folder inside `public_html`
- Add the photo of Professor Blevins's cat you downloaded to your `files-folders` folder on your computer *into* your `sandbox` folder by using the **Upload** button at the top of File Manager.
- Go to `https://yourdomainname/sandbox/prof-blevins-cat.jpeg` and see if the photo you just uploaded shows up!

### Create a new file in your sandbox folder

Now let's try adding a file into your `sandbox` folder that will show a very rudimentary webpage. 

- While still in File Manager, make sure you are inside your `sandbox` folder under `public_html` and click `+File` in the upper left, then name it `hello.html`. The `.html` ending tells File Manager what kind of file it is (in this case, an HTML webpage). 
- Make sure it is created *inside* your sandbox folder, then click Create New File. 
- You should see a new `hello.html` file now appear inside your sandbox folder. 
- Select the new HTML file you just created by clicking once, then click on HTML Editor towards the top of File Manager. 
- Click the Edit button that appears in a pop-up, and you should be seeing a blank screen with some buttons at the top. 
- Try writing a short message in the document, then click the Save button. 
- In a new browser tab, navigate to: `https://yourdomainnameurl/sandbox/hello.html` and you should see your message. Congratulations! 


### Bonus Activity: Embedding an image in an HTML file

- Make sure you are inside the `sandbox` folder in File Manager
- Create a new HTML file by clicking +File and naming 
it `cat.html`
- Open the new file using the HTML Editor button (ignore the warnings)
- Inside the HTML Editor, write "This is Professor Blevins's beautiful cat: "
- Click the `<>Source` button, and then copy and paste this line of code directly *before* the line in your file that says `</body>`: `<p><img alt="" src="http://cblevins.github.io/sp23-dig-stud/modules/prof-blevins-cat.jpeg" style="height: 267px; width: 200px;" /></p>`
- Go to `https://yourdomainname/sandbox/cat.html` and see if the page is showing an embedded photo. 

### Extra Special Bonus Activity: Making an Ugly Webpage

If you get done with everything above and your classmates are still working, go back to editing the `hello.html` file in the HTML Editor and try to make **the ugliest webpage you possibly can** (you can change the appearance of text using various buttons along the top row - ex. color, bold, etc.). Send your ugly webpage contestant to the `#in-class` Slack channel.