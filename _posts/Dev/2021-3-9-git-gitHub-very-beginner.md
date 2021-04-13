---
title: A Git And GitHub Tutorial For The Very Beginner
layout: post
section: DEV
permalink: /dev/git-github-tutorial-very-beginner/
author: Mostafa Lotfy
section: Dev
---


Git and GitHub are necessary skills to create your Jekyll website and add content to it. This article is part of [A Step By Step Guide To Start A Blog With Jekyll.](/dev/step-by-step-guide-start-blog-with-jekyll/){:target="_blank" rel="noopener noreferrer"} Here is the full list of skills you need to get familiar with before starting the step by step guide:

1. [The Command-Line.](/dev/command-line-very-beginner/){:target="_blank" rel="noopener noreferrer"}<br>
2. **Git & GitHub** <br>
3. `Markdown. (This post is coming soon)`<br>
4. `Jekyll. (This post is coming soon)`<br>

## **Why learn Git?**

**To host your website for free on [GitHub Pages](https://pages.github.com/){:target="_blank" rel="noopener noreferrer"}.** You need to learn how to use Git locally (on your computer), then to push (upload) your work to GitHub, which will then bring the changes you made locally to your website. Later on, making changes to your website will not take much effort. You will have a simple workflow--you will open your text editor, make changes, then use a couple of short terminal commands, and these changes will go live.

Other reasons to learn Git:
  - **Use git branches to experiment** fast without messing up your main work.
  - As your skills grow, Git and GitHub will allow you to **collaborate with others.**
  - **Back up your projects** on GitHub.
  - Show your work. **GitHub acts as a portfolio for software developers.**
  - **Learn from other people's work.** GitHub hosts many open source projects that you can download (clone) and learn from.

It will take you less than an hour to learn the basics and to start using Git today!


## **So, What is Git?**

**Git is software that is used to track changes made inside a folder.** When you add, remove, or modify files inside a folder where Git is initialized, it tracks all these changes. Git allows you to save these changes, ignore them, or get back to an old version that you have saved before. So Git is a version control software as it makes it easy to create and manage versions of your projects.

**Git allows you to experiment by creating parallel folders called branches.** You can switch seamlessly between your main branch and your other branches. You can choose to keep the changes you make in those branches or discard them.

**Git allows you to collaborate with others.** By pushing (uploading) changes you made from your local repository (a folder on your computer) to a remote repository (An online folder) and pulling (downloading) the changes others made from the remote repository to your local repository.

Git is mostly used by software developers to track their code, but it can track any folder containing text files.

## **And, What is GitHub?**

**GitHub is a website and online service where people share their git-tracked folders.**

When you work on your computer, your git folders are known as local repositories.  Git allows you to push (upload) your local repositories online to what is known as a remote repository. GitHub can host your remote repositories, either in public repositories, where others can see and use your work or in private repositories. You can work offline locally, then push and pull saved git files to and from your remote repository.

**GitHub is more than just a host for your remote repositories.** It allows you to use Git functions online. You can make changes, commit (save those changes to git), create branches, and more.

**GitHub also makes collaboration easier.** It lets you work with other individuals on projects and allows many people to work on open-source projects.


**There are other online services** where you can host and manage your git repositories like Gitlab. Also, there are services where you can host your static websites like Gitlab, Netlify, and many others. But GitHub is a good start point, then you can try other services as your skills grow.


## **How Does It Work?**

The best way to eliminate the confusion is to go ahead and try git, then things should start to make more sense.

Git is a command-line tool. Therefore **this tutorial is dependent on understanding the command line basics.** If you have not already, go through [the command line tutorial for the very beginner](/dev/command-line-very-beginner){:target="_blank" rel="noopener noreferrer"} before you start. Otherwise, you will feel lost. If you're already familiar with the command line, you can [refer to the command line cheat sheet](/dev/command-line-cheat-sheet/){:target="_blank" rel="noopener noreferrer"} if you need to.

**Any folder that you have on your computer you can track with git.**

Here is a list of mini-tutorials that you'll find below

- [Install Git and create a GitHub account](#install)
- [Start working with git locally](#start-locally)
- [Push your commits to GitHub](#push)
- [Pull commits from GitHub](#pull)
- [Create git branches](#branches)
- [Handle git conflicts](#conflicts)
- [Cehckout previous git commits](#checkout)
- [Clone a GitHub repo](#clone)




### <a name="install"></a> Install Git and create a GitHub account

1. Install Git.

    ```

    $ git --version     # Check to see if git is already installed on your computer. If you get a version number, it is.

    ```

    If Git is not installed, [download and install it](https://git-scm.com/downloads){:target="_blank" rel="noopener noreferrer"}.

2. Set username and email.

    ```

    $ cd ~                  # Navigate to your home directory.
    $ ls -a                 # List all files including hidden files.
    $ open .gitconfig       # Open the hidden file .gitconfig in a text editor.

    ```

    Add your user name and email to the `.gitconfig` text-file, then save and exit. The file should look like this:

    ```

    [user]
        name = your-user-name
        email = your-email
        
    ```

3. Create a GitHub account.

    Finally, [Create a GitHub account.](https://github.com/join){:target="_blank" rel="noopener noreferrer"}

    Your email must be the same one you set on Git! Double-check to make sure they are identical! To avoid linking issues between your local and remote repositories.

    When you push (upload) your work to your remote repository hosted on GitHub, you will be prompted in the command-line for a username and password. For security reasons, GitHub uses something called a personal access token in place of a password. This is a code that you can generate through your GitHub account. It gives you access to control your GitHub repositories using applications, including git.

    To create a personal access token, follow [this short and easy guide by GitHub.](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token#creating-a-token){:target="_blank" rel="noopener noreferrer"}. You'll be presented with multiple checkboxes. It's enough to tick the repo box.


### <a name="start-locally"></a> Start working with git Locally

Overview

You will create a new folder, turn it into a git repository, create files inside it, and commit them to git (save them to git).


1. **Create a new folder**<br>

    ```

    $ cd ~/documents    # Navigate to documents
    $ mkdir git-demo    # Create   a new folder and call it `git-demo`
    $ cd git-demo       # Navigate to your new `git-demo` folder.

    ```

2. **Turn the folder into a git repository**

    To turn any folder on your computer into a git repository, navigate to the folder using the terminal and run the `$ git init` command.

    ```

    $ git init          # This will initialize your folder and turn it into a git repository.

    ```

    When git is initialized, a `.git` hidden folder is created.

    ```

    $ ls -a               # You will find a hidden .git folder has been created. This means that Git is now tracking your folder.

    ```

3. **Check the state of the files in your folder**

    ```

    $ git status        # Show the state of files inside your git repo.

    ```

    A file can have different states: untracked, modified, staged, or committed.

    Untracked: Git sees the file but does not track its content. For Git to start tracking the file, you must add it to git first.

    Modified: Files that git tracks have been modified by adding or removing text to them. Git sees these changes, but they are not added to git (prepared to be saved) nor committed to git (saved) yet.

    Staged: After a file is modified, you can add it to git (stage it to be committed). It's prepared to be committed and saved to git. This is a state before saving where you can choose to stage multiple files to be committed together, to be part of the same commit.

    Committed: A File is tracked, and changes have been made to it. Those changes have been committed (saved) to git. Those committed files are saved, and you can revert to them at any time. A commit is like creating a version of your file in its current state. At any moment in the future, you can return to this version or just check it out.

    Committed files do not show when you use git Status. To see a list of all the commits you've made in a specific repository. Navigate to it and use the `$ git log` command.

    You will receive an error that this branch, which is called `master`, has no commits yet.

4. **Create Some Text Files**

    Create some empty text files inside your folder.

    ```

    $ touch index.md about.md blog.md

    ```

    `.md` means this is a Markdown file. Markdown is a file that includes text, and so git can track its content.

    This is just an example. It does not matter what files you create. Just create a couple of empty files.

    Check the status again. And note the difference.

    ```

    $ git status     # You have three untracked files, nothing stagged (prepared to be committed), and nothing committed.

    ```

5. **Add files to git**

    ```

    $ git add *

    ```

    Writing `*` after the `$ git add` command will add all modified and untracked files to git. You can specify which files to add by writing their names after `$ git add`,  like this: `$ git add index.html about.html`.

    Run `$ git status` again, and note the difference. Now, all three files are added/stagged to be committed. No untracked files.



6. **Make your very first commit!**

    ```

    $ git commit -m "initial commit"        # commit all stagged files with the commit message "initial commit"

    ```


    Every commit must have a commit message for yourself and others to read in the future to understand what the commit is about. It should be brief.

    You can commit all stagged files together, like the example above. Or you can choose which files to commit by writing the name of the files after the commit message. Example: `$ git commit -m "create empty file" index.md`.

    `git commit` is the command. `-m` is an option that allows you to add a message while making the commit, write the message after the `-m` option, then name the file you want to commit. If you want to commit all files, do not name any specific file, but everything staged will be committed.

    Now check the status and log, again!

    ```
         
    $ git status    # You have no stagged files and no untracked files.

    ```

    To check all commits you've made in this repo:

    ```

    $ git log   # You have one commit.

    ```

    You can see the author of the commit, the date it was committed, and which branch you're at. You also have a commit hash, which is a number next to the commit, that you can use to check out this commit later on.

    If you want more info about the commit, you can use `$ git log --stat` to get a list of modified files.

    You now have your first version.

<br>

### <a name="push"></a> Push to GitHub

You will connect your local folder to a remote folder, which will be an online repository you create on GitHub. Then you will push your commits from your local to your remote repository.

Only committed changes will be pushed. This means that untracked, modified, and stagged files will not be pushed. This means that if you make a change to a file in a local repo and do not commit this change to git it will not be uploaded to your remote repository. Even though you can see the change when you open the file. Unless you commit a change, git will not push it.

1. **Create a new empty GitHub repo**

    [Follow the `Create a repository` part in this guide by GitHub.](https://guides.github.com/activities/hello-world/#repository){:target="_blank" rel="noopener noreferrer"}

2. **Connect your local folder to your new GitHub repo**

    Copy the URL of your new GitHub repository. After the command `$ git remote add`, name your remote repo, then paste the URL.

    ```

    $ git remote add origin https://github.com/mstflotfy/gitHubTutorial

    ```

    A local folder can be connected to multiple remote repositories. Using this command, you add this remote repo to the list of repositories this local git folder can push and pull from. `origin` is the default name of the main remote, but you can call it anything you want.

3. **Push your commits to the remote repo on GitHub**

    ```

    $ git push -u origin master

    ```

    Later on, you'll just use `$ git push` the rest of the command is only the first time, to make this specific remote repository the one you automatically push to.

    `origin` is the name of the remote repo, and `master` is the name of the branch you'll push from.

<br>

### <a name="pull"></a> Pull from GitHub

You'll make changes online on GitHub then pull those changes to your local repo.


1. **Make a commit in your remote GitHub repo**

    Go to your GitHub repo. You'll find all the files you've committed locally and pushed. Click on one of the files and follow the [Make a commit section in this GitHub Guide](https://guides.github.com/activities/hello-world/#commit){:target="_blank" rel="noopener noreferrer"}

    It does not matter what you write, just add text to the file and make a commit.



2. **Fetch Changes**

    Ues `$ git status`, and you'll notice that the local folder is unaware of the changes you made online to your remote repo. As it will say that your branch is up to date with origin/master, which is the main branch in your remote GitHub repo.

    ```

    $ git fetch     # Fetch the changes but do not commit them yet.

    ```

    Git fetch does not pull the changes but makes your local folder aware of them so that you can either apply them or ignore them.

    ```

    $ git diff master origin/master    # Compare the local branch master to the remote branch origin/master

    ```

    The remote repository is called `origin`, it has one branch called master. Our local repo has one branch that is called master. So you are comparing the branch master in your local repo to the branch master in your remote repo.

    You'll see deleted lines in red with a `-` sign before them and added lines in green with a `+` sign before them.

3. **Merge**

    Merge the commits you made on GitHub to your local repo.

    ```

    $ git merge

    ```

    The commit you made on GitHub will now also be committed locally.

    If you're sure you want to commit the changes and want to skip fetching and checking first. You can pull commits directly with the `$ git pull` command.


<br>


### <a name= "branches"></a> Create git branches

A branch is like a duplicate that you create of your main branch. You can switch to this duplicate and make changes that will not show up in your main branch unless you merge them in. This allows you to experiment fast and switch quickly between your different branches.


1. **Create a new branch**


    To create a new branch just type the command `$ git branch` followed by the name you want to give your new branch.

    ```

    $ git branch test         # create a new branch and call it `test`.

    ```

    ```

    $ git branch              # Display all local branches.

    ```

    The branch you're currently at will be marked with a star.

2. **Switch to the new branch**

    ```

    $ git switch test         # You'll switch to the test branch. If you use `git branch`, you'll find `test` in green and marked with a star.

    ```

3. **Make a commit in the new branch**

    ```

    $ touch test.md

    ```

    Create a new Markdown file and call it `test.md`.

    You created the `test.md` file in the test branch, but it is not tracked with git. Therefore, if you use the `ls` command in the main or test branches, the file will show up.

    Make sure you're at the `test` branch, then add and commit the `test.md`.

    ```

    $ git add test.md
    $ git commit -m "Create an empty file at test branch"

    ```

    Now your branch test will have one commit. When you use the `ls` command when you're in the `test` branch you'll be able to see the file `test.md`, if you switch the main branch and use the `ls` command the file will not show anymore.

    You can use the command `$ diff master test` to see what the differences are between the two branches.

4. **Merge the new branch in your main branch**

    To bring changes to a branch from other branches switch to the branch you want to bring changes into, and type the name of the branch you want to bring changes from after the command `git merge`

    ```

    $ git switch master     # Switch to the master branch.
    $ git merge test        # Merge branch test into master.

    ```

    If you use the `ls` command in the master branch the test.md file will now show up and if you run the command `git log` you'll find the commit you've made in the test branch now brought to the master branch.


<br>


### <a name="conflicts"></a> Handle a merge conflict

Conflicts happen when you change the same parts of the same file differently in different branches then try to merge them.

1. create a new branch and call it `conflict`

    ```

    $ git branch conflict

    ```

2. Switch the `conflict` branch.

    ```

    $ git switch conflict

    ```

3. Modify the file test.md

    Modify the file test.md by adding a line of text to it.

    Either `$ open test.md` and write down a line of text in it, then save and close. Or just use the `echo` command to insert a line of text in it.

    ```

    $ echo "Here is some text" >> test.md

    ```

4. Add and commit the change in the `conflict` branch

    ```

    $ git add *
    $ git commit -m "Add some text to create a conflict"

    ```

    This change is committed to the `conflict` branch but not to `master`. If you switch to the master branch and look at the test.md file you will not find the line of text you just added in the `conflict` branch. To read the content of the test.md inside the terminal, use the `cat` command:  `$ cat test.md`

5. Switch to the master branch: `$ git switch master`

6. Add a different line of text.

    ```

    $ echo "Here is some conflicting text" >> text.md

    ```

    Now test.md exists on both branches master and conflict yet it has conflicting content on each.

 7. Try to merge the `conflict` branch into the master branch.


    ```

     $ git merge conflict

    ```

    Git will tell you to go sort your business first before you come back again!

8. Open the file to see the conflict and handle it.

    Git will help you by adding conflict markers, but you must open the file and manually resolve conflicts.

    It should look something like this:

    ```

    <<<<<<< HEAD
    Here is some conflicting text
    =======
    Here is some text
    >>>>>>> conflict

    ```

    The `=======` part separates your conflicting parts. The upper part marked as `HEAD` is the branch you try to merge into--the master branch. And the part below comes from the `conflict` branch.

    You can keep one of the two or combine them manually. Or remove both, and type something else.

    remove the whole block above and add this line: `Here is some text to resolve the conflict`

9. **Add and commit.**

    Now, you need to add and commit your resolved conflict in the master branch.

    ```

    $ git add test.md
    $ git commit -m "resolved merge conflict"

    ```





<br>


### <a name="checkout"></a> Checkout a previous commit

When you make a commit, you make a version of the current folder that you can check out in the future. You might, at some point, want to have a look at one of the previous versions of a git repo. You can just have a look, or you can create a new branch for that version.

1. **List previous commits**

    ```

    $ git log       # shows a list of all commits.

    ```

2. **Copy the commit hash**

    There will be a long number next to each commit. Copy the number next to the commit you want to checkout, select the number, and press `cmd + c`.

3. **Check out the commit**

    Paste the number after the `$ git checkout` command using `cmd + v`

    ```

    $ git checkout pasteTheNubmerHere

    ```

    You can make changes as you like by adding or removing text.


4. **Keep or discard your changes**

    When you use this command Git will explain to you exactly what you can do. Basically, Git creates a temporary branch for you with the old commit, where you can have a look around and make changes that will not affect your other branches. To get back to your main branch, and discard your changes just switch to one of your branches: `git switch master`.


    If you want to keep the changes, you will need to create a new branch to save them in:

    ```

    $ git switch -c newBranch    # This will create a new branch, called newBranch, and save the version you're checking out in it.

    ```

<br>



### <a name="clone"></a> Start from a clone

You might prefer to **use someone else's work as a starting point rather than starting from scratch**. When you find a GitHub repo that contains a project you'd like to use as a starting point, fork this repo, turn it into a template, and use this template to make a new repository. Then clone (copy) this new repo and use it locally.

#### But what is a fork?
A fork allows you to have a copy of a project on GitHub. This copy or fork is connected to the project it was forked from. When the owner of the repo makes changes, you can pull them. You can make changes to your fork, but you can't directly make changes to the main repo you forked. If you want, you can suggest changes, something called a pull request. You are basically making a request from the owner of the original repo you forked to pull the changes you made in your fork to the main repository. Making these changes a part of the project. The owner can review your pull request, discuss it with you, then accept or reject it. As a beginner, this is not something you're likely to do.

Yet, you might want to use a repository owned by someone else as a starting point for your project, with no intention to contribute to the main project. In this case, after you fork the repository, turn it into a template to separate it from the main project (the one you forked it from) and make it your own.

#### What is a clone?
Cloning a repository is like downloading it. It will create a local git repository that is the same as the repository you cloned. And it will be connected to it. You can pull and push changes directly to and from this repo.


1. Fork a repo

    Go to the page of any public repository, that you do not own, and press the `fork` button.

    If you don't have a repo you want to fork. You can fork the repository of my [Jekyll website.](https://github.com/mstflotfy/mstflotfy.github.io){:target="_blank" rel="noopener noreferrer"}


2. Turn your fork into a template

    Go to the settings of the repository. Under the repository check the `Template repository` checkbox. You can follow [this guide by GitHub](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-template-repository){:target="_blank" rel="noopener noreferrer"}.


3. Create a new repo from the template

    Go to the main page of the repo, by clicking on its name, or on the `< > code` button. Then click on the green button `Use this template`. Then, it's like creating a new repository. [More on this.](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template#creating-a-repository-from-a-template){:target="_blank" rel="noopener noreferrer"}

    Now notice only one initial commit is shown.

4. copy the URL

    Copy the URL of the repository you created from the template.

5. Clone it locally

    Using the terminal, navigate to the folder where you want to place the repo that you will clone. Let's say to Documents. `$ cd ~/Documents`

    ```

    $ git clone pasteUrlHere

    ```

    A new folder will be created with the name of your GitHub repo, you can `cd` into it. It will be connected to the GitHub repo so you can push and pull directly.



<br>


## **Still confused?**
Other resources I found useful.

[GitHub Official Guides](https://guides.github.com/){:target="_blank" rel="noopener noreferrer"}<br>
[Pro Git Book](https://www.git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository#ch02-git-basics-chapter){:target="_blank" rel="noopener noreferrer"} <br>
[A step by step intro to Git](https://www.freecodecamp.org/news/what-is-git-and-how-to-use-it-c341b049ae61/){:target="_blank" rel="noopener noreferrer"} <br>
[A quick youtube video that shows the git workflow](https://www.youtube.com/watch?v=USjZcfj8yxE){:target="_blank" rel="noopener noreferrer"} <br>
[Youtube video explaining the workflow between git and gitHub](https://www.youtube.com/watch?v=nhNq2kIvi9s){:target="_blank" rel="noopener noreferrer"}<br>
[Youtube video explaining git and showing workflow](https://www.youtube.com/watch?v=HVsySz-h9r4){:target="_blank" rel="noopener noreferrer"}<br>
[Bitbucket Git Tutorials](https://www.atlassian.com/git/tutorials/learn-git-with-bitbucket-cloud){:target="_blank" rel="noopener noreferrer"}<br>

<br>

Back: [The Command Line Cheat Sheet](/dev/command-line-cheat-sheet/) | Next: [A git cheat sheet](/dev/git-cheat-sheet/)<br>
