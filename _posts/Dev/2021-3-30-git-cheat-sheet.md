---
title: Git Cheat Sheet
layout: post
section: Dev
permalink: /dev/git-cheat-sheet/
author: Mostafa Lotfy
section: Dev
---

![A git doodle I made for this article.](/assets/i/gitCheatSheet.jpg "Git Doodle"){:oncontextmenu="return false;"}


**On This Page**

- [Install And Configure](#install)
- [Working with Local Folders](#local)
- [Working with Remotes](#remote)
- [Working with Branches](#branches)
- [Handling Conflicts](#conflicts)
- [Documentation and Help](#docs)
- [Other Git Cheat Cheets](#other)

---

Anything between `< >` is a variable part of the command. It changes according to the naming of your files and branches.

## <a name="install"></a> **Configure**


{% highlight bash %}

 $ git --version         # Check if git is installed on your system and check its version.

{% endhighlight %}


{% highlight bash %}

 $ open ~/.gitconfig     # Open `.gitconfig`--a hidden file at the home directory--and edit username and email.


{% endhighlight %}


{% highlight bash %}

 $ open .git/HEAD       # Rename a branch by switching to it,  open the `HEAD` file in the `.git` hidden folder, and edit the line `ref/heads/master`. Change the last part of the line, which is the current branch's name.

{% endhighlight %}

## <a name="local"></a>**Working Locally**

{% highlight bash %}

 $ git init              # Turn any local folder into a git repo.

{% endhighlight %}

{% highlight bash %}

 $ git status            # Check untracked, modified, or added files.

{% endhighlight %}

{% highlight bash %}

 $ git log               # list of all commits.

{% endhighlight %}

{% highlight bash %}

 $ git add <file>        # Stage a file to make it ready to be commited.

{% endhighlight %}

{% highlight bash %}

 $ git add <file1> <file2>       # Stage multiple files to commit them together.

{% endhighlight %}

{% highlight bash %}

 $ git add .             # `.` or `*` to stage all modified and untracked files.

{% endhighlight %}

{% highlight bash %}

 $ git commit -m "commit message" <file>             # Commit a specific file from the staged files. And add a commit message.

{% endhighlight %}

{% highlight bash %}

 $ git commit -m "commit message" <file1> <file2>    # Commit mutliple files.

{% endhighlight %}

{% highlight bash %}

 $ git commit -m "write a commit message"            # Commit all stagged files at once and add a commit message.

{% endhighlight %}


## <a name="remote"></a> **Working with Remotes**

{% highlight bash %}

 $ git clone <url>       # Clone a repository to a local folder from a url. Example: `$ git clone https://github.com/mstflotfy/mstflotfy.github.io`

{% endhighlight %}

{% highlight bash %}

 $ git remote            # Get a list of all the names of remote repos you've specified.

{% endhighlight %}

{% highlight bash %}

 $ git remote --v        # Get a list of all remotes with their URLs.

{% endhighlight %}

{% highlight bash %}

 $ git remote add <origin> <url>     # Add a new remote repository.

{% endhighlight %}

{% highlight bash %}

 $ git push <origin> <branch>        # Push new commits from local branch to a remote repo. Example: `$ git push origin master`.

{% endhighlight %}

{% highlight bash %}

 $ git push -u <origin> <branch>     # Push commits and set a specific remote as the default remote to push and pull from.

{% endhighlight %}

{% highlight bash %}

 $ git push      # Push to the default remote.

{% endhighlight %}

{% highlight bash %}

 $ git fetch     # Fetch changes from the default remote without committing them. Can use `$ git diff` afterward to look at changes.

{% endhighlight %}

{% highlight bash %}

 $ git pull      # Pull commits from default remote to the local branch and commit them.

{% endhighlight %}

{% highlight bash %}

 $ git remote show <origin>      # Show more info about a specific remote.

{% endhighlight %}

{% highlight bash %}

 $ git remote remove <origin>    # Remove a remote by deleting the reference to it.

{% endhighlight %}

## <a name="branches"></a> **Wroking with branches**

{% highlight bash %}

 $ git branch            # Show all local branches.

{% endhighlight %}

{% highlight bash %}

 $ git branch --all      # Show branches, including remotes.

{% endhighlight %}

{% highlight bash %}

 $ git branch <new-branch-name>  # Create a new branch. Example: `$ git branch testBranch`

{% endhighlight %}

{% highlight bash %}

 $ git switch <branch-name>      # Switch to a specific branch. Example: `$ git switch main`

{% endhighlight %}

{% highlight bash %}

 $ git diff <branch1> <branch2>       # Show the difference between two branches. Example: `$ git diff master origin`

{% endhighlight %}

{% highlight bash %}

 $ git merge <branch>        # Merge branches. Merge changes from named branch into the current branch.

{% endhighlight %}

{% highlight bash %}

 $ git branch -d <branch>    # Delete a branch.

{% endhighlight %}

{% highlight bash %}

 $ git checkout <commitHash>         # Cheackout an old commit in a headless branch. Then git will walk you through what to do.

{% endhighlight %}

## <a name="conflicts"></a> **Handling conflicts**

- Git will pause the committing process until the conflicts are resolved.
- Run `$ git status`. You'll find files with conflicts listed as `unmerged`.
- Git will add conflict-resolution markers to files containing conflicts.
- Open the files and resolve the conflicts manually and remove the markers.
- Conflicting parts from different branches will be separated by `=======`.
- Choose one side or merge the content manually.
- Run `$ git add` on each file to mark it as resolved.
- Then, you can run `$ git commit` to commit the files.



## <a name="docs"></a> **Help & Docs**

[Official Git Documentation](https://git-scm.com/docs){:target="_blank" rel="noopener noreferrer"}


{% highlight bash %}

 $ git --help <verb>     # Docs for a specific command. Example: `$ git --help add`

{% endhighlight %}

{% highlight bash %}

 $ git <verb> -h         # Get a short list of some options for a command.

{% endhighlight %}

## <a name="other"></a> **Other Cheat Sheets**

- [A git cheat sheet by GitHub.](https://training.github.com/downloads/github-git-cheat-sheet/){:target="_blank" rel="noopener noreferrer"}
- [A git cheat sheet by GitLab.](https://about.gitlab.com/images/press/git-cheat-sheet.pdf){:target="_blank" rel="noopener noreferrer"}
- [A git cheat sheet by Tower.](https://www.git-tower.com/blog/git-cheat-sheet/){:target="_blank" rel="noopener noreferrer"}
- [A git cheat sheet by freeCodeCamp.](https://www.freecodecamp.org/news/git-cheat-sheet/){:target="_blank" rel="noopener noreferrer"}

<br>

Previous: [git & GitHub Tutorial](/dev/git-github-tutorial-very-beginner/)  | Next: `Markdown (This post is coming soon)`
