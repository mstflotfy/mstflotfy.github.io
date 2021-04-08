---
title: A Command Line Tutorial For The Very Beginner!
layout: post
permalink: /dev/command-line-beginner-tutorial/
author: Mostafa Lotfy
section: Dev
---

This article is part of [A Step By Step Guide To Start A Blog With Jekyll.](/step-by-step-guide-start-blog-with-jekyll/){:target="_blank"}

The commands in this tutorial work on Mac and Linux. If you are using Windows, you will have to look up [how to install bash on Windows.](https://duckduckgo.com/?q=how+to+install+bash+on+windows&t=h_&ia=web){:target="_blank"}

There is no need to memorize any command. Understand what each one does and how to use it. Then use a [cheat sheet](/command-line-cheat-sheet/){:target="_blank"} when you get stuck. After a while, you will memorize the commands you repeatedly use.

## Outline

Parts 1-3 is the minimum you need to know.

1. Open the Terminal
2. Navigate
  - $ ls
  - $ cd
  - $ pwd
  - $ clear
3. Command Structure
3. Edit
   - $ open
   - $ touch
   - $ nano
4. Organize
  - $ mkdir
  - $ rm -r
  - $ mv
  - $ cp
  - $ du
5. Be More Efficient
  - Wildcards (*)
  - aliases
  - minimal look ($ )
  - $ man

One last thing before you start, a directory is just a folder.

## **Open the terminal**

Press `cmd + spacebar`<br>
Type `Terminal` and press enter<br>

Use `cmd + tab` to swiftly switch between the terminal and your browser.

You will be met by an almost empty screen with a few lines. Ignore everything and focus on the `$` sign. It indicates that you can type a command on this line. It is not a part of your commands, just an indication of where they are.

## **Navigate**

You will use the command line to navigate through the files and folders on your computer.

<br>

#### **$ ls**
`ls` is short for list. Write it after the `$` sign to get a list of all files and folders in the directory where your terminal is open. The result should look something like this:

{% highlight bash %}
$ ls
Applications		Desktop			Downloads		Movies			Pictures		Tresors			progRelated.kdbx
Creative Cloud Files	Documents		Library			Music			Public			iCloud Drive (Archive)
$ |
{% endhighlight %}

Command outputs have no `$` sign before them. A new line will appear after the list, starting with the `$` sign, where you can type a new command.

`ls` is a command, but commands can have options.

Using a Mac, if you want to create a hidden file, you just add a `.` before its name. For these hidden files to be listed when you use `$ ls` you need to add an option to the command.

An option is preceded by a dash ( `-` ). To show your hidden files in the list, you will add the `-a` option to your command. Like this:

{% highlight bash %}
$ ls -a
{% endhighlight %}

The hidden files will be listed with a `.` before their name.

Now list all the files and folders in your current working directory using the `ls` command on its own. Then list them again, showing all the hidden files.

<br>

#### **$ cd**

`cd` is short for change directory.

{% highlight bash %}
$ cd Destination
{% endhighlight %}

After the `$` sign, write the command `cd`. `$ cd` by itself does nothing. It needs a destination to change to.

To navigate to a folder inside your working directory,  just type its name. You are in the home directory. If you want to change the folder your terminal is working at to the Documents folder, you can use this command:

{% highlight bash %}
$ cd Documents
{% endhighlight %}

If you want to change the directory/folder to home again, you can write `..` after `cd` as the destination. It is a bit like tapping back on mac and more like tapping up in Windows when navigating your folders using the user interface.

{% highlight bash %}
$ cd ..
{% endhighlight %}

Get familiar with this way of navigation. Using `$ ls` to see what files and folders are inside the current working directory, `$ cd folderName` then `$ cd .. ` to move back.

Now, what if you navigate to Documents, then to another folder inside Documents, and navigate deep inside your folders. If you want to get back to the home directory, you will have to use `$ cd ..` and `$ ls` multiple times.

Instead of doing that, you can simply use this command to change to the home directory from anywhere you are:

{% highlight bash %}
$ cd ~
{% endhighlight %}

Remember that to navigate to a folder, you need to write a destination. When that folder is inside your current working directory, you just type its name. If the folder is in a different directory, you need to provide a destination or a path to your desired folder.

A path starts from the root directory. The root directory is defined by the `/` sign, which you can use as its destination. Think of it as the top folder in your drive, and every other folder is underneath it. You need to give a path all the way down from the root to your desired folder.

The home folder has this shortcut `~`. When you write the command `$ cd ~`, it is the same as `$ cd /Users/yourUserName`, which is the path or the destination to your home folder.


Likewise, if you want to navigate directly to your Documents folder, all you need to do is type this:

`$ cd /Users/yourUserName/Documents`

to make it simpler, you can write this instead:

`$ cd ~/Documents`

This allows you to change your directory with one line instead of using `cd`, `cd ..` and `ls` multiple times.

If it's still unclear, here are some other examples:

To change the directory to Downloads, you need to write its destination. Since Downloads is inside the home directory, you can simply do this:

`$ cd ~/Downloads`

If you want to go to a folder called newFolder inside the Desktop directory, you can do it this way:

`$ cd ~/Desktop/newFolder`

Now play around. Navigate to folders, list everything, and navigate to other folders, back one step. Also, navigate using destinations, and when you are done, go back to the home folder using `$ cd ~`

You can also right-click on any folder and choose `New Terminal at Folder`, or type `cd` and drag and drop a folder to the terminal to make it the current working directory.

<br>

#### **$ pwd**

`pwd` stands for print working directory. What `pwd` does is show you the destination of the folder your terminal is open at. This will be your working directory--the commands you write will mainly apply to the files and folders inside it.

{% highlight bash %}
$ pwd
{% endhighlight %}

Write the command `pwd` just after the `$` sign. <br>

A new line will appear under your command with its output. It should look something like this:<br>

{% highlight bash %}
$ pwd
/Users/yourUserName/
$ |
{% endhighlight %}

Whenever you are not sure where you are, just write the `pwd` command.

<br>



#### **$ clear**

Whenever your terminal screen gets crowded by commands, type `clear` to go back to a peaceful and empty terminal window. This might be a good time for it.

<br>

## **Command Structure**

Now that you are familiar with different commands to use as examples. Let's breakdown the command structure to eliminate any left confusion.

`$ command -options arguments`

`pwd` is a command.<br>
`ls` is another command.

`ls -a` is a command that has an option `-a`.<br>
`ls` lists files and folders inside our working directory, and `-a` is an option that includes hidden files in our list.

{% highlight bash %}
$ cd ~/Documents
{% endhighlight %}
`cd` is the command, but it needs an argument (input). It needs a destination to change the working directory to,  `~/Documents` is the argument that the command requires.

Multiple options and arguments could be put together.

Go to your home directory `$ cd ~`. List the elements inside `Documents` without changing the working directory to Documents. Using this command:
`ls Documents`

Here `ls` is the command, and Documents is the argument, which is the input to the command.

You are still at the `~` directory. List the elements inside of `Documents` again, but include the hidden files in the list this time.

{% highlight bash %}
ls -a Documents
{% endhighlight %}

`ls` is the command that will list files and folders in your current working directory. While`-a` is an option that tells the terminal to include hidden files as well in the list.  `Documents` is an argument that makes the terminal apply the command on the `Documents` folder instead of the current working directory.

<br>

<br>

## **Edit**

Now that you can navigate. Let's learn how to do quick edits to text files.

#### **$ cat**
{% highlight bash %}
$ cat newFile.txt
{% endhighlight %}

This command will display the content of a text file inside the terminal. A quick way to examine the content of text files without a need to open the file itself.


#### **$ touch**
{% highlight bash %}
$ touch newFile.txt
{% endhighlight %}

This command will create a new empty text file with the name you type after it, inside the current working directory off course.

To create a new empty text file in a different directory, you need to add a destination:

{% highlight bash %}
$ touch ~/Desktop/newFile.txt
{% endhighlight %}

This command will create a new empty text file called `newFile` in the Desktop directory.


Check if the file has been created. Get a list of all files and folders on your Desktop using this command:

{% highlight bash %}
$ ls ~/desktop
{% endhighlight %}


#### **$ open**
{% highlight bash %}
$ open fileName.txt
{% endhighlight %}

`Open` is a command that can be used on files or folders. This command will take you away from the command line to a new window of the file you chose to open. You can navigate back to the command line using `cmd + tab`.

To open the newFile.txt you just created in the `Desktop` folder, use this command:

{% highlight bash %}
$ open ~/desktop/fileName.txt
{% endhighlight %}

Edit the text file, when done press `cmd + s` to save, close it, then use `cmd + tab` to return to the terminal. This is useful if you want to do a quick edit to a text file.

The files you open do not need to be text files. You can open any kind of file you want. Make sure you add the file extension after the file name. For example: fileName.pdf, fileName.txt, fileName.jpeg, ...

Open can also be used to open folders in Finder. Just add the folder address after the open command instead of a file name. `$ open ~/Documents`

When opening a file, that's in the current working directory, all you need to do is write its name, including the extension.

If you want to open a file that is in another directory, you can write a destination like this:

{% highlight bash %}
$ open ~/Documents/Books/file.pdf
{% endhighlight %}

More likely, you will not know the file name, but you might know its destination. In that case, you might navigate to its destination first:
`cd ~/Documents/Books`

then use `$ ls`

then `$ open file.pdf`

otherwise, you can just type

`open ~/Documents/books`

And the Books folder will open in Finder.


#### **$ nano**
{% highlight bash %}
$ nano fileName
{% endhighlight %}

We can use nano to read text files or create new text files. If the name we write after nano exists in the current working directory, it will open the file. Otherwise, it will create a new file.

The current screen will switch to the contents of the file. You can read, add a line or two, then press `ctrl+x` to exit.

You will be asked to save the changes type `Y` or `N`.

Then you will be prompted again to choose a name for the file. Just press enter, and the changes will be applied. If you change the file name, a new file will be created with the changes.

Use nano on the newFile.txt you created on the Desktop. Either navigate first to the Desktop then use `$ nano newFile.txt` the file or just open it in one line since you already know it's there:

{% highlight bash %}
$ nano ~/desktop/newFile.txt
{% endhighlight %}

Write anything you want and then press `ctrl + X`, read the prompt, and then press 'Y'. Read the prompt, then press: enter.

Try this again, but this time don't write anything or make any changes.

Try for the final time and change the name of the file while saving.

You can use `nano` to make quick text edits or quickly read the contents of a file, without switching between the text editor and the terminal.



## **Organize**

To open a folder in Finder, type `$ open FolderName`.

I find it useful to open the terminal and Finder in windows next to each other and use whichever I feel is more productive for the task. It does help when organizing to see what your commands are doing.

#### **$ mkdir**
{% highlight bash %}
$ mkdir newFolderName
{% endhighlight %}

`mkdir` stands for make directory. It creates new folders. Obviously, it needs a name for the folder to be created, which we will write after the `mkdir` command.

If you want to create a folder in a different directory, then you will need to add the destination.

Create a folder called newFolder inside `Documents`. Either navigate to Documents first using `$ cd Documents`, then create the folder using `$ mkdir newFolder` or just type this command:

{% highlight bash %}
$ mkdir ~/Documents/newFolder
{% endhighlight %}

If you want to see if the folder is actually created, you can use `$ ls` if you're already in the Documents directory or anywhere you are type this:

{% highlight bash %}
$ ls ~/Documents
{% endhighlight %}

#### **$ rm-r**
{% highlight bash %}
$ rm -r folderName
{% endhighlight %}

`rm` stands for remove. It is used to delete files. Adding the option `-r` to it will also make it delete folders with everything in them. Therefore you should be careful when using it as it will delete a folder with all the files and folders inside it without asking for confirmation.

Using `mkdir`, create multiple folders within each other.  Then remove all of them with the `rm -r` command.

#### **$ mv**
{% highlight bash %}
$ mv oldName newName
{% endhighlight %}

`mv` stands for move. We can use it to cut and paste a file or folder. We can also use it to rename.

You can also think about it this way: `$ mv source destination`.

Create a new folder in the Documents directory and name it oldName. You can use this command: `$ mkdir ~/Documents oldName`

Move the oldName folder from Documents to Desktop:

`$ mv ~/Documents/oldName ~/Desktop/oldName`

As you can see, you will first type the source of the folder you want to move, then next to it, type the destination where you want to move it.

If the destination is your current working directory. If you are already in Documents, you can just write the command this way:

`$ mv oldName ~/Desktop/oldName`

As the source is assumed to be the current working directory.

You can move and rename at the same time:

`$mv oldName ~/Documents/newName`

When moving files, remember to write the extension after the name:
`$ mv fileName.jpeg ~/Documents/photos/fileName.jpeg`


To just rename a folder, make the destination the same as the source:

`$ mv file.jpeg newName.jpeg`

or

`$ mv ~/Documents/oldName ~/Documents/newName`


#### **$ cp**
{% highlight bash %}
$ cp fileName Destination
{% endhighlight %}
`cp` is to copy. Again you can think abou it this way `$ cp source destination`.

Navigate to the Desktop folder:
`$ cd ~/Desktop`

Create a text file and name it file.txt in the Desktop directory: `$ touch file.txt`

Create a new folder and name it folder in the Desktop directory: `$ mkdir folder`

Copy file.text into folder: `$ cp fie.txt folder`

Duplicate file.txt and name the duplicate file2.txt: `$ cp file.txt file2.txt`


If you know the address of the file you want to copy and the address where you want it to be, you don't need to navigate there. You can do something like this: `cp ~/Desktop/file2.txt ~/Documents/file2.txt`

The cp command, by default, works on files. If you want to copy folders, add the
`-R` option to the command like this example: `$ cp -R folder1 ~/Documents/folder1`

#### **$ du**
{% highlight bash %}
$ du -sh *
{% endhighlight %}

`du` stands for disk usage.

This will give us the size of each file and folder in our current directory.

If you use the `du` command with no options or arguments, the result will be unreadable. Adding the `-s` option displays only main files and folders. The `-h` option means human-readable and shows the size using common symbols like `G` for Gigabyte. The `*`  applies this command to every file and every folder within the current working directory.

If you write the command without`*` you will get the total size of the current working directory.

## **Be More Efficient**

#### **Wildcards**
{% highlight bash %}
$ cd  Doc*
{% endhighlight %}

The `*` sign is called a wildcard.


If we are the home directory. The above command would take you to `Documents` without the need to finish writing the full name, just write a part of the name that makes it unique, then use the `*` sign for the rest. This literally means change the working directory to the folder that starts with the letters `Doc`

To tell the terminal which file or folder a command will apply to, we need to write the name of this file or folder. Wildcards could be utilized to save time and energy when writing those names.

Create a new folder in the Documents Directory that has the name: `aFolderThatHasAVeryLongName` using this command:

`mkdir ~/Documents/aFolderThatHasAVeryLongName`

Navigate to Documents and try to change the directory to `aFolderThatHasAVeryLongName`.

Ok, now get back to Documents using `cd ..`

Here are a couple of ways to use wildcards to navigate to this ridiculously long-named folder without needing to type the full name:

`cd aFolder*`

`cd *LongName`

`cd *AVery*`

And you could probably come up with better ones. Notice how wild cards are used to fill in the blanks. It doesn't matter how you write it as long as it's written in a way that identifies the specific file you want. Wildcards replace any part of the input that you're too lazy to write.

It can also be used with extensions.

If you want to see a list of all the text files in your current directory: `ls *.txt`
If you want to copy all pdf files: `cp *.pdf'

Be careful if you use mv and rm with wildcards. If you do something like this: `rm -r *` every file in your current directory will be deleted without asking for confirmation!


#### **Aliases**

{% highlight bash %}
$ alias jkld='bunlde exec jekyll serve -drafts'
{% endhighlight %}

An alias is a shortcut to a command. Instead of typing the command, you set an alias to write a shorter version.

Here is how to create your own alias:  `$ alias name='command'`


I use the command `$ bundle exec jekyll serve -drafts` many times each day.

I created an alias for it using this command:

`$ alias jkld='bundle exec jekyll serve -drafts'`

Now when I type `$ jkld`, the command `$ bundle exec jekyll serve -drafts` is executed. I did not have to call it `jkld`, it's just the name I chose, I could have called `jd` instead if I wanted to:

`$ alias jd='bundle exec jekyll serve -drafts'`

But using an alias this way has a problem. It only works for this current terminal session. This means if I exit the terminal and open it again and type `jkld` expecting it to give me the result of `$ bundle exec jekyll serve -drafts`, nothing would happen.  I would have to first run this command again each time I open the terminal: ``$ alias jkld='bundle exec jekyll server'`` then I can use `$ jkld`.

The solution is simple. I will write my aliases in a file that the terminal loads before each session. Then I can just use `jkld` directly anytime I open the terminal.

The terminal you are currently using is probably either bash or zsh. If you are not sure which one you have type any random letters and you'll get an error message showing you which one it is. It should like this:

`$ kjkjkj
zsh: command not found: kjkjkj`

If you have bash then add your alias commands to the text file .bash_profile. If you have zsh add your aliases to the text file .zshrc. Both files are in the home directory.

Let's create a simple alias that you can remove later if you do not like it. You will make an alias for the command `$ cd ..` that allows you to write `$ ..` instead to get the same result.

First, open the file that the terminal loads before it starts. It's a text file, so open it using the `open` command, edit it, then close it. You can also use `nano` if you want.

`$ open ~/.bash_profile`

or

`$ open ~/.zshrc`

Add this line to it, without the `$` sign.

`alias ..='cd ..'`

Press: `ctrl+s` to save, close the file, then `ctrl+tab` to return to the terminal.

now  close and reopen the terminal and try to use `..` instead of `cd ..`

I also use an alias to navigate to certain folders by doing something like this:

`alias folder='cd ~/Documents/folder'`

Now all I need to do is type `$ folder`,  and I'm there.

If you are too lazy to use aliases you can try `ctrl+r` to search your past commands.

#### **Tabs**

You can have multiple tabs in a terminal just like you do in a browser. Jut press `cmd + t` to open a new tab. If you have to restart your terminal you can open a new tab instead.



#### **A minimal look**

`ps1='$ '`

For the sake of a minimal look, I removed everything before the dollar sign by adding this line above to either the .bash_profile file if using bash or .zshrc file if using zsh. These are files that the terminal loads before every session.

You'll need to restart or open a new tab to see changes.

#### **Dealing with spaces**

{% highlight bash %}
$ cd 'folder Name'
{% endhighlight %}


If there is a file or folder that has space in their name, for example: `file 1.txt` instead of `file1.txt` you can wrap their name like this: ``'file 1.txt'``

Here's another example:

`$ touch 'new file.txt'`

#### **$ man**

{% highlight bash %}
$ man du
{% endhighlight %}

Use `$ man anyCommand` to go to the manual and understand how it works. It will be unreadable and complicated at first, and you will think it's useless. But in time, you will get used to it, and it will be handy.

#### **alt + click**

To get the mouse cursor to a specific part of a sentence or command in a terminal you need to press and hold the `alt` button while doing it otherwise it will not work.

#### **tab for autocomplete**

Instead of writing the whole name of a file or folder or using a wildcard, you could instead use press on the tab button for autocomplete, after writing the intial par of the name.


<br>

If you are a hardcore learner I suggest you repeat the little exercises in this tutorial while using wildcards. Also, make aliases for the folder or two that you visit the most on your computer. And Use the `man` command on each of the commands you use.

Remember not to try to memorize commands it will happen automatically. You can refer to the command line cheat sheet when you get stuck.

---

<br>

[Back: The Command Line](/command-line-very-beginner/)<br> | [Next: The command line cheat sheet](/command-line-cheat-sheet/)
