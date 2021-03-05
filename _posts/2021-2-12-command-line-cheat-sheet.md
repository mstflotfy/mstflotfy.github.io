---
title: The Command Line Cheat Sheet
layout: post
permalink: /dev/command-line-cheat-sheet/
layout: redirected
redirect_to: https://dev.mstflotfy.com/command-line-cheat-sheet/
---

This article is part of [A Step By Step Guide To Start A Blog With Jekyll.](/step-by-step-guide-start-blog-with-jekyll/)


## **Navigate**

#### **$ ls**

{% highlight bash %}
$ ls    # list all files and folders inside your current working directory. The current working directory is the folder where your terminal is open.
{% endhighlight %}

{% highlight bash %}
$ ls -a   # Include hidden files in the list.
{% endhighlight %}

#### **$ cd**

{% highlight bash %}
$ cd folderName   # Change the current directory to a folder inside it. Example: `cd documents` changes the directory from `~` to `Documents`.
{% endhighlight %}

{% highlight bash %}
$ cd ..   # Move up one directory. Example: `cd ..` changes the directory from `~/Documents` to `~/`.
{% endhighlight %}

{% highlight bash %}
$ cd ~    # Navigate to the `home` directory. The `~` sign is a shortcut to `/Users/yourUserName/`.
{% endhighlight %}

{% highlight bash %}
$ cd ~/Documents    # Make any folder your current working directory by writing its path from the root `/` directory or from the home `~` directory.  This command will make `Documents` the current working directory.
{% endhighlight %}

{% highlight bash %}
$ cd /    # Make the root folder the current directory.
{% endhighlight %}

#### **$ pwd**

{% highlight bash %}
$ pwd   # Print Working Directory. Know which directory your terminal is open at. Get a path from the root `/` folder down to your current working directory.
{% endhighlight %}

#### **$ clear**

{% highlight bash %}
$ clear    # Clears the terminal screen.
{% endhighlight %}

## **Command Structure**

#### **$ command -options arguments**

{% highlight bash %}
$ ls -a Documents   # `ls` is the command, `-a` is an option, and `Documents` is the argument.
{% endhighlight %}



## **Edit**

#### **$ cat**
{% highlight bash %}
$ cat file.txt   # Read a text file inside the terminal.
{% endhighlight %}

#### **$ open**
{% highlight bash %}
$ open file.txt   # Open a file or folder inside the current directory. You can edit the file, save it, then get back to the terminal. Also, opens Folders in `Finder` and any type of file. When opening a file, the extension must be added after the name.
{% endhighlight %}

{% highlight bash %}
$ open file.pdf   # Open any type of file. Add the extension to the end of the name.
{% endhighlight %}

{% highlight bash %}
$ open folder   # Can open folders in `Finder`. Example: `$ open ~/documents` opens the documents folder in `Finder`.
{% endhighlight %}


#### **$ touch**
{% highlight bash %}
$ touch newFile.txt   # Create a new empty text file inside the current directory.
{% endhighlight %}

{% highlight bash %}
$ touch ~/desktop/newFile.txt   # Create a new empty text file inside any directory by adding a path. This command will create a new text file named newFile.txt on the Desktop folder.
{% endhighlight %}


#### **$ nano**
{% highlight bash %}
$ nano fileName   # Create, read, or edit a text file inside the terminal. `ctrl+x` to exit, `Y` to save changes, then confirm the name of the file.
{% endhighlight %}

{% highlight bash %}
$ nano ~/desktop/fileName   # Create or edit a text file directly on the `Desktop` without changing the current working directory to Desktop first.
{% endhighlight %}

#### **$ echo**
{% highlight bash %}
$ echo "line to add" >> <fileName>   # Add a line of text to a file on the fly (without opening the file)
{% endhighlight %}

{% highlight bash %}
$ echo "alias ..='cd ..'" >> ~/.zshrc   # Add an alias directly without the need to open or navigate.
{% endhighlight %}


## **Organize**

#### **$ mkdir**
{% highlight bash %}
$ mkdir newFolder # Create a new folder in the current working directory. Stands for make directory.
{% endhighlight %}

{% highlight bash %}
$ mkdir ~/Documents/newFolder   # Create a new folder inside `Documents` without changing the current working directory to `Documents`.
{% endhighlight %}


#### **$ rm-r**
{% highlight bash %}
$ rm -r folderName    # Delete files or folders without asking for confirmation!
{% endhighlight %}


#### **$ mv**
{% highlight bash %}
$ mv Source Destination   # Move a file or folder from source to destination.
{% endhighlight %}

{% highlight bash %}
$ mv ~/Documents/folder1 ~/Desktop/folder1    # Cut and paste between two different directories. Move the folder `folder1` from Docouments to Desktop.
{% endhighlight %}


{% highlight bash %}
$ mv folder1 ~/Desktop/folder1    # Cut and paste from the current working directory. Move the folder `folder1` from the current working directory to the Desktop.
{% endhighlight %}


{% highlight bash %}
$ mv fileName.jpeg newFileName.jpeg    # Rename in the same folder.
{% endhighlight %}


{% highlight bash %}
$mv oldName ~/Documents/newName    # Move and rename, from the current directory to Documents.
{% endhighlight %}


{% highlight bash %}
$ mv ~/Documents/oldName ~/Documents/newName    # Rename files and folders in any directory. Rename a folder in Documents.
{% endhighlight %}


#### **$ cp**
{% highlight bash %}
$ cp Source Destination # Copy a file or folder, from a source to a destination.
{% endhighlight %}

{% highlight bash %}
$ cp file.txt folder # Copy a file into a folder. Both are inside the current directory.
{% endhighlight %}


{% highlight bash %}
$ $ cp file.txt file2.txt   # Duplicate file.txt inside the current directory and name the duplicate `file2.txt`.
{% endhighlight %}

{% highlight bash %}
$ cp ~/Desktop/file2.txt ~/Documents/file2.txt   # Copy a file from a directory to another without changing the current directory. file2.txt will be copied from Desktop to Documents.
{% endhighlight %}


{% highlight bash %}
$ cp -R folder1 ~/Documents/folder1   # Copy folders, by adding the `-R` option to the `cp` command. The `cp` command works on files by default. To make it work on folders, add the `-R` option.
{% endhighlight %}

#### **$ du**

{% highlight bash %}
$ du -sh    # Get the total size of the current directory.
{% endhighlight %}

{% highlight bash %}
$ du -sh ~/Documents    # Get the total size of any directory writing its address.
{% endhighlight %}

{% highlight bash %}
$ du -sh *    # Get the size of each file and folder in the current directory.
{% endhighlight %}

{% highlight bash %}
$ du -sh ~/documents/*    # Get the size of each file and folder in any direcotry.
{% endhighlight %}


## **Be More Efficient**

#### **Wildcards**
{% highlight bash %}
$ cd  ~/Doc*    # Use wildcards to be lazy and avoid writing long names. This command will change the current directory to the `Documents` folder. Could also just press tab for autocompletion.
{% endhighlight %}

{% highlight bash %}
$ ls *.pdf    # Use wildcards creatively with other commands to do more. This command will only list pdf files inside our current directory.
{% endhighlight %}



#### **Aliases**

{% highlight bash %}
$ alias name='command'    # Shortcuts to write a shorter version to a command.
{% endhighlight %}

{% highlight bash %}
$ alias ..='cd ..'    # Make an alias `..` as a shortcut to `cd ..`
{% endhighlight %}

To make an alias permenant add it to one of those text files:<br>
`~/.bash_profile` <br>
`~/.zshrc` <br>

#### **Tabs**

`cmd + T` To open a new tab.

`cmd + 2` Cmd and the tab number, to switch between tabs.



#### **A minimal look**

{% highlight bash %}
ps1='$ '    # Remove everything before the `$` sign by adding this line to the `.zshrc`, or `.bash_profile` files.
{% endhighlight %}


#### **Dealing with spaces**

{% highlight bash %}
$ touch 'new file.txt'    # Wrap the name of a file or folder in '' if they have spaces in their names.
{% endhighlight %}


#### **$ man**

{% highlight bash %}
$ man du    # Use the `man` command on any command to open the manual and read more about how it works.
{% endhighlight %}


#### **alt + click**

`alt + click`  To specify where to write instead of using the keyboard arrows.


<br>

Remember not to try to memorize commands it will happen automatically. You can refer to the command line cheat sheet when you get stuck.

---

<br>

[Back: A command line tutorial for the very begginer](/command-line-beginner-tutorial/)<br> | Next: `Git & GitHub. (coming soon)`
