Version control with *git* in RStudio
=======================================

## and *collaborative* version control with *Github* ##

<br>

**John Stanton-Geddes**

**7 March 2014**

--------------------------------------------------------

[Version control](http://en.wikipedia.org/wiki/Revision_control) is the structured management of changes to files. In science, version control is invaluable for keeping detailed changes to analyses, especially of "big" data that can be difficult to recreate. [git](http://git-scm.com/) is a popular open-source version control program with considerable support in the biological community. Though a command-line based program, you can access most of the power of `git` from the graphic-user interface (GUI) of [RStudio](https://www.rstudio.com/ide/docs/version_control/overview). 

Version control can (and at first, should) be used strictly locally on your own computer. Once you are comfortable using `git` for version control locally, you can start sharing your code and collaborating with others using an online platform such as [Github](https://github.com/). Github is also well-supported by biologists. There are many advantages to syncing your local version control repository to a public repository on github, including easy sharing of code, feedback from colleagues, and public visibilty. 

In Part 1 of this tutorial, I explain how you can set-up and use `git` for version control of your analyses in RStudio. Once you've masterd `git` locally, you can move onto Part 2 where I explain how you can share and collaborate on code using [Github](https://github.com/).

For more on why you should use version control, see this paper

Ram, K. (2013). [Git can facilitate greater reproducibility and increased transparency in science. Source Code for Biology and Medicine, 8, 7.](http://www.scfbm.org/content/8/1/7/abstract)

## Setup

To get started, install [Rstudio](http://www.rstudio.com/) and [git](http://git-scm.com/) on your computer. 


## 1: using version control in RStudio ##

1. Open RStudio and start a new project 
	- File --> New Project --> Empty Project 

2. Initialize version control using `git`
	- Tools --> Version Control --> Project Setup

This will open the "Project Options" window. Specifify `git` as your version control system, and confirm that you want to initialize a new git repository. Restart Rstudio. A new file ".gitignore" will be added to your directory (more on this below). 

4. In the "Environment, History, ..." pane you should now see a "Git" tab. Click on this and you will see three columns: "Staged", "Status" and "Path". The "Staged" column has check boxes under it. You will click these when you have files ready to commit (or save). The "Status" column first two are the important ones. As you have no files currently under version control, you should see ? symbols under status for all files in your directory.

3. Open a new Rmarkdown (.Rmd) or Sweave (.Rnw) script. Edit! Save.

6. To start tracking a file, click the box in the "Staged" column next to the file. The "Status" column should change to a green "A" which means you've added to file to your version control tracking. Do *not* track the .Rproj file (we will 'ignore' this below). 

7. Your files are "staged" or ready for tracking, but you haven't yet committed these changes. To do so, click the `Commit` button in the git window. This will bring up a commit window. The top left pane summarizes which files you've staged for this commit, the bottom pane shows additions (in green) and deletions (in red) made to the currently selected file in the summary pane. In the top right, add your "Commit message". Something like "Started new script in version control for analysis". Be as detailed as possible. Then click `Commit`. This will pop-up a new window that summarizes your commit. Close the "commit" window. 

8. Open the .gitignore file and add a line with ".Rproj". Save and close this file. The .Rproj file should no longer appear in your git window. In your "git" window, the .gitignore file should now appear with an "M" indicating it has been modified.

9. Modify your files, stage and commit the changes as before. Open the commit window, and select the "History" tab at the top. Now you can see a summary of the changes to your script!

10. Now you have your script under version control locally!



## Part 2: using version control collaboratively ##

A major benefit of version control is that you can share your code, or work collaboratively on the same version-controlled directory.

To do this, you first need an account on [www.github.com] or one of the similar websites. Github is well-developed and has a strong user-base in the bioinformatics world. You should review the basic instructions for [using github](https://help.github.com/). Though the free tier of github is publically accessible, you can pay for private repos or create your own using Dropbox.

You'll make a 'repository' on github, which is just like a directory on your own computer but other people can 'clone' or 'fork' your repository. 

1. Log into your github account and click "New repository".  Give it a useful name.

2. Initialize the repository a README describing what the repository is for. I'd also recommend adding a default `.gitignore` file as suggested by github. 

3. At this point, you have a blank repository online. To get it onto your computer, open RStudio.  Select Tools --> Version Control --> Project Setup.

4. In the box labeled "Origin", paste the URL of the github repository you just created:

    https://github.com/USERNAME/REPO.git

5. Now you have a RStudio project and you can go about adding R scripts and data files. 

6. Follow the directions above to track your files using `git` and commit your changes. 

7. All right, now you want to 'push' your changes to the remote repository you created on github. To do this, open the commit window. At the top right, you should see two buttons, `Push` and `Pull`. Clicing `Push` will open a window that 'pushes' your repository to github. 

8. After each commit, it's good practice to push your changes. If multiple collaborators are working on the same project, make sure you `pull` any changes that may have been made while you were working before `push`ing your own changes.


Remember - keep the source code under version control, but not the results. These can (and should) always be recreated with your source code.



## Cloning an existing repository ##

What if you want to use someone else's code (that they've kindly shared) or collaborate with someone that has already started a repository? This is easy as well. 

1. Open Rstudio and start a new project

2. Select "Version Control: Checkout a project from a version control repository"

3. Select your version control of choice (e.g git) and provide a URL to the repository

4. Done! Git will automatically "clone" the contents of the repository and you can begin editing. From the commit window, you'll also be able to `push` changes back to the origin.
    - **Note**: unless you intent is to work collaboratively on a shared repository, you should first [fork](https://help.github.com/articles/fork-a-repo) the repository to your own github account, and then clone your forked repository. 



