# How to make a static site by using static site generator and host it onto a forge
- This guide is for **technical documentation newbies** (such as developers and technical writers who need to host their resumes), and demonstrates how to build a modern technical documentation system through lightweight markup language (Markdown), distributed version control (Git), static website generator (Pelican), and code hosting platform (GitHub Pages). This guide follows the core principles proposed by _Andrew Etter_ in "_Modern Technical Writing_":
- **Simplicity first**: only include necessary steps
- **Toolchain standardization**: use lightweight tools
- **Maintainability**: separate content and style
- **Collaboration-friendly**: open contribution process

---

## Prerequisite 
Before you begin, make sure you have:
- a [GitHub](https://github.com/) account
- Locally installed [Git](https://git-scm.com)
- [Python](https://www.python.org)
- Some markup language basics (if you don't, here is a [tutorial](https://www.markdowntutorial.com))

## Step 1.1 Install Python
First, you need a computer, visit the official website of Python, and download the latest version. When installing, remember to check Add Python to PATH, and then follow the instructions during the installation. After the installation is successful, Windows users can enter the command ```python --version``` in the terminal. When it displays the version number, it means you have succeeded.

## Step 1.2 Install Pelican
After installing Python, you need to install pelican. Pelican is a static site generator based on Python. To install it, you need to enter ```python -m pip install "pelican[markdown]"``` in the terminal and wait for a while for Pelican to be installed.

## Step 2.1 Initialize the Project
Now that we have installed Pelican, enter the command ```mkdir <your folder name>``` in the terminal to create the folder where you need to store your resume, then enter the command ```cd <your folder name>``` to go to the folder you just created, and then enter the command ```pelican-quickstart``` to quickly generate a static site. Enter the appropriate answer according to the questions that appear to complete. For details, please check the [official website of Pelican](https://getpelican.com/).

## Step 3.1 Add content
Now you have your own static site. In the folder you just created to store your resume, you may see several files, namely Makefile, pelicanconf.py, publishconf.py, tasks.py and two folders, content and output. Click to enter the content folder, where we can put our resume in the site. Create a new text document, name it resume and open it. Now you need to write your resume in markup language, for example

```
---
title: (your name)
date: (today's date)
---
(Your introduction can be written here)
```

Remember to save it after writing, and then change the suffix of this file to .md instead of .txt. Now you have your own resume site.

## Step 3.2 View you site
Now what we need to do is to check our resume site to check whether the markdown format of our resume is correct. Open the terminal and enter ```cd <you folder name>``` to go to the folder where you store your resume site, then enter ```pelican content``` to let Pelican process the resume that needs to be put into the site for us, and then enter ```pelican --listen```, it will give us a site address, similar to ```https://126.0.0.1:8000```, copy and paste it into the browser to open it and you can see your personal resume site.

## Step 4.1 Make repository in GitHub
Next you need a forge to host your site. You can choose GitHub, which is the most widely used platform in the world. Open the browser to enter GitHub, log in to your own account, or register a new account, click the plus sign in the upper right corner, and click New Repository to create a new repository that can host our site. You can name it ```yourname.github.io```, select Public as the visible scope, and do not need to select the initial README file. So you have a repository that can host the site.

## Step 4.2 Move your resume to repository
Now you need to move the contents of the resume folder to the repository you just created. First, you need to install ghp-import. Enter ```python -m pip install ghp-import``` in the terminal. Then you need to initialize git. Enter ```git init```, then enter ```git add .``` to package your resume, and then enter ```git commit -am "First commit"```. Next, you need to enter the following code to add a remote repository for remote operations ```git remote add origin [URL of the remote repository]```, and then enter the following code to generate the site and deploy it to GitHub:

```
pelican content -s publishconf.py
ghp-import output -b gh-pages
git push origin gh-pages
```
Then you can see the contents of your resume folder in your repository. After doing this, you can click Settings->Pages to see the URL of your resume website.

## FAQ
- Q: Why is Markdown better than writing raw HTML?
-  A: Because it is more concise and more readable.
-  Q: I changed the Markdown version of my resume, so why don’t I see the changes when I refresh the website in my browser?
-  A: If you made changes in the original folder, you need to re-enter ```palican content``` to let Pelican process it, and then re-upload it to GitHub

## Contributors
Zheng Ren   
instructor: Tristan Miller   
TA: Peter Vu   
