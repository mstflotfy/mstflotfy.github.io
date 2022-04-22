---
title: What is the command line? Why learn it? And Just Enough To Get Started!
layout: post
author: Mostafa Lotfy
section: Dev
permalink: /dev/command-line-simplified/
description: I am on a learning journey to build my own apps. I started it by exploring Figma, now I think I need to move on to coding, and I think that learning the command line is a great starting point. This is my cmd line study notes. I tried to simplify getting started with the cmd line.
---

![I tried to simplify getting started with the command line](/assets/i/v12/v12-iD-th5.png)

<br>
<br>

While the command line seems like a scary and daunting place, getting started with it is not as hard as it first seems. In the following video, I try to simplify getting started with the command line. This article contains notes from the video. I tried to be brief with the article, not sure it worked, but I think that this is a thorough (for an intro that is) introduction to the command line, that can take you from knowing nothing about the command line, to confidently using it daily. And hopefully, build up your knowledge from there.

<br>
<br>

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/wRsqiMIBI3Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>  
  

## Outline

*You can come back to the outline by pressing the back button of your browser.*

[1. What is the command line?](#what)  
[2. Why should you care? Why I'm learning it?](#why)  
[3. How to start?](#how)  
[4. Navigate](#nav)  
[5. Organize](#org)  
[6. Edit](#edit)  
[7. Customize](#cust)  
[8. What's Next?](#next)  

## 1. What is the cmd line? {#what}

We use a GUI (Graphical UI) to interact with our computers.

Another way to interact with a computer is using text.

The command line takes your text commands and passes them to your system to perform them.

The command line, Shell, Terminal, and Bash are different things, but for now, just think of them as the app that allows you to interact with your computer using text.

But why would you want to do that? Why should you **even** bother?

## 2. Why learn the command line? {#why}

*This video/article does not aim to promote abandoning GUI and using the cmd line to do every single thing. But to show you that learning the command line can be easy and can make you more efficient with some of your everyday tasks.*  

### Speed & Efficiency

The terminal allows you to do some of your everyday tasks in a faster and more efficient way.

How? 

In this article's video, I give an example of that. My Desktop was a mess. I gave a quick example showing how I'd normally clean up my Desktop using **GUI**, then I did it again using **the terminal**. A trivial example. But, to me, it was clear that using the terminal is the more efficient (and even enjoyable) option out of the two. 

Many other everyday tasks can become more efficient by using the terminal. Especially if you're doing something repetitive or dealing with a large number of files. 

### You want to become a developer

Start doing everyday things using the command line, and get used to interacting with your computer using text, which is something a developer does all day.

A good entry point to get into the mindset of a developer, get closer to the Dev environment, and get familiar with Dev tools.

Learn to take control of your computer then learn to program.

### Dev Tools

If you intend to develop you'll eventually have to use Dev tools, and some of those tools do not have a GUI. And so, you'll need to learn to use the command line, at least the very basics of it, to be able to use these tools.

It's a skill that you'll need to learn anyway if you want to build your own apps.

An example of this I wanted to create a website and made a quick research online and found the best way for me was to [host my website for free](/dev/how-to-start-a-blog/) using [GitHub pages](https://pages.github.com){:target="_blank" rel="noreferrer"} and use a tool called [Jekyll](https://jekyllrb.com){:target="_blank" rel="noreferrer"} to build the site, and a tool called [Git](https://git-scm.com){:target="_blank" rel="noreferrer"} to upload my pages online using one command. Both Jekyll and git are command line tools. 

Another example, I want to use [NextJs](https://nextjs.org){:target="_blank" rel="noreferrer"} to make webapps, when I go to its [Docs](https://nextjs.org/docs/getting-started){:target="_blank" rel="noreferrer"} it will refer me to to install it using the command line.

A third example, I came across a very interesting tool called [remotion](https://www.remotion.dev){:target="_blank" rel="noreferrer"}, that allows you to use code to make animations and edit vids. Again, to install it and use it, I had to use the command line.

A fourth example. I came across another tool called [revealjs](https://revealjs.com){:target="_blank" rel="noreferrer"}. It allows you to use HTML or Markdown to make presentations that look great, just by typing some text! And I also had to use the cmd line to install it and use it.

### Not just Dev Tools

Package managers are like app stores for the terminal.

[Homebrew](https://brew.sh){:target="_blank" rel="noreferrer"} is the most popular package manager for mac computers, and APT for linux, but there are other package managers for both systems.

Through package managers, you can download and install tools, that you can use daily. Some of those tools are not just for developers.

For example, I can install a command-line internet speed test tool on a mac using one command: `$ brew install speedtest-cli`.  And I can test my internet speed through the command line without visiting any website or downloading any app, using a single quick command: `$ speedtest`.

You can also use a package manager to download and update GUI apps using one-line commands. 

I can install Figma from the command line using one line of code: `$ brew install --cask figma`, or install Brave Browser: `$ brew install --cask brave-browser`.

### Finally getting started is not as hard as it first seems

It's just another tool that you'll learn.

Even GUI apps need learning and some are not very intuitive, even more, difficult to use than the terminal.

You'll use a cheat sheet at first to help you memorize the commands you use the most, and when you repeatedly use commands, you'll use a cheatsheet less often. 

At first, you'll just do simple tasks, that you can already do using GUI, using the terminal. But, as you develop your knowledge you'll be able to do what is not possible to do using GUI.

You'll also become faster and more efficient at doing some of your everyday tasks.

## 3. How to start using the command line? {#how}

If you're using a Mac or Linux, you can simply open the **terminal App** and get started immediately! 

On a Mac, I press *cmd spaceBar* to open **Spotlight search**, type *terminal*, and press **return**. And I can start writing commands.

If you're using windows there are 2 ways you can use a Linux Shell:
	
1. [Install git for windows](https://gitforwindows.org/){:target="_blank" rel="noreferrer"}, which runs a Linux shell emulator.
2. [Install Windows Subsystem for Linux](https://gitforwindows.org/){:target="_blank" rel="noreferrer"}, which is the way that is most recommended. It gives you a Linux environment without using a virtual machine or dual-booting Linux.

## 4. Navigate {#nav}

Now that you're inside the **terminal app**. The first thing you can do is use the **terminal** to navigate through the files and folders on your computer.

![blank.png](/assets/i/blank.png)

When you open **the terminal** you get a **prompt**, it might look different depending on your settings. Usually, you'll find a `$` sign and a fat rectangle. 

The `$` sign is a **prompt** it shows you that this is **a command line**. You can type your command after the prompt. The rectangle is just **the cursor**.

### `pwd` - print working directory

![pwd.gif](/assets/i/pwd.gif)

To know where you're at, type your very first command: `pwd`: Print working directory. Think of a directory as just a folder. Basically, you're telling the terminal to show you what folder you are at, right now.

`pwd` returns a path for you. Then the prompt and cursor again, show you that you can type another command if you want.

`/Users/mostafalotfy/`  is the absolute path to where I am currently at, my home folder.

But what is an absolute path?

### Linux Directory Structure And Absolute Paths

![linuxDs.gif](/assets/i/v12/linuxDs.gif)

Everything (all files and folders), in a Unix-based system, is located under the **root** directory `/`.

Therefore a full path to any file or folder starts from the **root**. This is called an **absolute path**.

The **home directory** is a directory that holds your personal files and folders. It contains folders like **Desktop**, **Downloads**, **Documents**, among other things. 

In a Linux system the **absolute path** to the **home directory** is like this: `/home/userName`. 

For mac, it's the same (Since it's a Unix-based system), but your personal files will be under `/Users/yourUserName`. 

So, the path returned by the `pwd` command `/Users/mostafalotfy`, is the path to my home folder. It's like directions, start from the **root** directory `/`, then move to the **Users** directory `/Users`, then move into my user. 

The home directory has a shortcut to it `~`. For example, the absolute path to my **Desktop** will be `/Users/mostafalotfy/Desktop` or `~/Desktop`.

If I have an image on my **Desktop** named **screenShot1.png**. The absolute path to it will be `~/Desktop/screenShot1.png`


### `ls` - list directory contents

![ls.gif](/assets/i/v12/ls.gif)

Use the `ls` command to know what files and folders are inside your current working directory.

`ls` will return a list of all files and folders inside your current directory.

`ls -<options>` You can add options to the `ls` command.

`ls -a` The `-a` option will include dotfiles, which are hidden files, in the list.

There are many options for the `ls` command. `ls -G` will give colored output, which will make directories have a different color than files. 

Most options can be combined. This is how I often use the `ls` command: `ls -GhalS`

### `clear` - clear the terminal screen

![clear commmand](/assets/i/v12/clear.gif)

When the screen gets too crowded you can use the `clear` command to get back to the comfort of a blank screen.

### `man` - display manual pages

But how to know what options you can use with your commands?

![man command](/assets/i/v12/man.gif)

Use the `man` command followed by the command you want to know more about. And you'll get all the info on this command, including a list of all options you can use. 

Can be confusing at first, but keep using it and you'll learn how to extract what you need out of it.

No need to learn every option, just look for what you need.

If you run the command `man ls`, you can read what each of the options I use with the `ls -GhalS` command does.

- `-G` gives colored output, so folders have a different color than files. 
-  `-a` shows hidden files
- `-l` gives a long list with more info about the file. This will come in handy in the future as you expand your knowledge. Including file type, permissions, and file size.
-  `h` makes the size of files human-readable, by adding K for Kilobytes, G for Gigabytes, and so on. 
- `S` orders files according to size

Try to use the man command on each new command you learn. To quit the manual just press the `q` key.

I find it helpful sometimes to open the man in a new tab. By pressing `cmd t`, then `man <cmd>`, and switching using `cmd 1`  & `cmd 2` just like you would inside your browser.

### Anatomy of a command

What is the anatomy of a command line?



<!-- ![cmdAnatomy.png](/assets/i/cmdAnatomy.png) -->

```bash

$ <cmd> -<option> <argument>▮

```

- `$` The dollar sign is a prompt to show you that you can write a command here.
- `▮` This rectangle is just to show you where the cursor is at.
- `<cmd>` The cmd name. Like `ls`
- `<options>` Options that you can add to the command. Like `-G`
- `<arguments>` Inputs that some commands need to run. like a path to a file or directory. If the cmd is to list then I can give directories as input to be listed.

`$ ls -a ~/Desktop`, in this command, `ls` is the name of the command, `-a` is an option that will list hidden files as well, and `~/Desktop` is the argument, which is the directory that the command will apply to. So the command will list all files and directories inside the desktop directory, including hidden ones.


### Relative path

If you are at the home directory `~`. The Documents directory is already inside it, no need to give an absolute path, we can give a relative path instead. I can just do it this way directly: `ls Desktop`, This is called a relative path. 

If an absolute path uses the root as the reference, a relative path uses our current working directory as the reference. 

The current working directory is referred to with a `.`, so you can `ls .` but there is no need to write it here as the `ls` command already lists the current working directory if given no argument.

The parent directory is referred to using `..`. If your current working directory is the Desktop, and you `ls ..` this will list your home directory.

So, I can use the command `ls` with no arguments and it will list my current working directory. I can use it with a relative path as an argument `ls Documents` if I'm at the home directory. And, I can use it with an absolute path argument `ls ~/Downloads`. 

### `cd` - change working directory

`cd` Stands for change working directory. Use it to navigate through your folders, and to head to any folder on your computer. 

You can use a relative path; `cd Downloads`. 

Or an absolute path; `cd ~/Downloads` Or `cd ~/Desktop/screenshotsFolder`. You can jump to the *Downloads* folder (or any folder) even if it's not inside your current working directory.

`cd` by itself, with no arguments, takes you to your home directory.

`cd ..` goes to the parent directory.

`cd -` goes back so you can toggle between 2 folders.

### `open` - open files and directories

You can use the `open` command to open directories inside GUI.

`open .` Open the current working directory inside GUI.

`open ..` Open the parent directory using GUI.

`open ~/Desktop` Open any folder on your computer by giving an absolute path to its destination.

`open Documents` Use a relative path to open a folder. This is just like `open ./Documents`, using your current working directory `.` as the starting point instead of the root `/` directory.

If you have a `screenshots` directory at your Desktop, you can open it inside GUI, and look at the images by typing this: `$ open ~/Desktop/screenshots`

`open` can also be used to open applications by adding the `-a` option; `$ open -a Safari`

`open ~/Downloads/images/image1.png` The open command can also be used to open files.

## 5. Organize {#org}

Now that you know where you are, you can list files and directories, and you can navigate between directories, let's see how we can organize our directories and files.

### `mkdir` - make directories

`mkdir newFolder` This command will make a new directory named **newFolder** at the current working directory.

`mkdir ~/Desktop/newFolder1` You can give an absolute path to where your want to create your new directory. This command will make a directory *newFolder1* at the *Desktop*.

If you want to create a parent directory with multiple directories inside it with one command. Do it this way `mkdir -p files/images/screenShots`. This will create a new directory named **files** with another one inside it named **images**, then another one inside **images** named **screenShots**.

### `mv` - move files and directories

Now let's move things!

<!-- ![mv.gif](/assets/i/v12/mv.gif) -->

```bash

 $ mv <file> <directory>

```

```bash

 $ mv <file1> <file2> ... <directory>

```

Basically, the mv command takes at least 2 arguments or inputs, the path to the files you want to move, then the last argument should be the destination directory you want to move the file or files to.

`mv ~/Desktop/image.png ~/Documents/screenshots` This command will move a file with the name *image.png* from the *Desktop* folder to a folder named *screenshots*, which is inside the *Documents* folder.  

`mv image.png photo.png` We can also use the mv command to rename files or folders. This command will rename the file *image.png* to *photo.png*. 

`mv ~/Desktop/image.png ~/Documents/screenshots/myImage.png` You can move and rename a file at the same time.

`mv image1 image2 image3 image4 ~/.Trash` You can move multiple files from your current working directory to any folder you want on your computer. This command will move three files to a hidden folder/directory inside the home folder called `.Trash`.

One problem that can happen with the move command is that if you move a file that has the same name as another file, it will overwrite it, without asking for permission. If you want it to ask for your permission first before overwriting use the interactive option. `mv -i (interactive. Forces the mv command to request permission before overwriting.)`

`mv newFolder ~/.Trash` You can also move directories.

### `cp` - copy files and directories

```bash

 $ cp <file1> <file2> ... <directory>

```

Almost, just like the `mv` command but copies.  

`cp ~/Desktop/myBook.pdf ~/Documents/myBooks` This will copy the file *myBook.pdf* from the *Desktop* directory to to *myBooks* directory inside *Documents*.  

`cp -r myFolder myFolderDuplicate` Copying folders with the `cp` command requires adding the `-r` option. 

Also, you can rename while copying, and copy in the same directory to make duplicates. The `-r` option will copy folders with all files and directories inside them.  

Let's delete some shi*!

### `rmdir` - remove empty directories

```bash

 $ rmdir <directory>

 ```

The only thing this command does is remove empty folders. This could be useful if you have a bunch of empty folders you want to delete. You can run this command on all files and folders in a directory, knowing that only empty directories will be deleted. 

If I make a bunch of empty folders at the desktop `mkdir emptyFolder1 empty2 empty3 empty4`

I can then `rmdir *` to remove all empty folders. We'll talk about wildcards in a minute. For now, it just means apply this command to all files, and since **rmdir** only works on empty folders, nothing important will be lost.

### `rm` - remove files and directories

```bash

 $ rm <file>

 ```

```bash

 $ rm -r <directory>

 ```

To remove or delete files, or folders that are not empty use the `rm` command.

Be careful with this, as the files are not moved to the **trash** but removed permanently without asking for confirmation. And you can't get them back!

`rm ~/Documents/myImage.jpeg` This will remove the file **myImage.jpeg** from the **Documents** directory.

`rm -r ~/Desktop/myFolder` This will permanently delete the directory **myFolder** from the **Desktop** directory. The `r` option, stands for recursive, it will make the remove command delete a folder with all files and folders inside it. Be careful son!

To avoid accidents using the `rm` command, use the `mv` command instead to move the files and directories you want to delete into the system's trash folder, for mac, it's `~/.Trash`. This would allow you to restore your files or remove them safely.

### `Wildcards`

Wildcards will make your command apply to every file that matches a specific pattern.

There are different ways to make patterns, but usually, you can target files that end in a specific extension, like this `mv *.png` This command will permanently delete every single file that has the **.png** extension, that ends in **.png**, inside the current working directory. 

Or, you can target files that start with a specific word, like this `cp mstf* ~/Documents/myFiles`. This command will copy every file that starts with **mstf**, and send the copies to **myFiles** folder, in the **Documents** directory.

You can also target files that have a specific word in the middle -` ls *image*`. This command will list the contents of every directory that has the word **image** in the middle of its name.

Be careful using this! If you make a mistake you can mess up a lot of files.

## 6. Edit {#edit}

Almost done! It's time to edit files using the command line, text files especially, as those are the ones you'll deal with the most as you develop your own Apps.

### `touch` - create a file

```bash

 $ touch <file>

 ```
Creating a new text file using GUI can take some steps, using the command line you can create a text file, or a bunch of them, on the fly.

`touch newFile.txt file2.md file3.js file4.md` This will make a bunch of files for you, inside your current working directory.

Obviously, you don't need to be inside the folder to make a new file there. If I want to create a new file at the **Desktop** using an absolute path, I can write this command `touch ~/Desktop/newfile.txt`. 

### `open` - open files

```bash

 $ open <file>

 ```

The first way to edit a text file is to open the file using GUI and edit it.

`open file.txt` This will open **file.txt**, using the default app and you can edit it and save it, then get back to the terminal.

### `cat` - concatenate and print files

```bash
 
 $ cat <file>

```

Use the `cat` command to have a quick peek inside text files.

It stands for concatenate, to link or connect together. But, its simplest use case is a quick peek into a text file.

No need to open the file then it will display inside your terminal. 

### `echo` - return arguments 

<!-- ![echo.gif](assets/i/v12/echo.gif) -->

Echo is a simple command that returns whatever argument you give it. It takes your input and turns it into output. This might, at first, seem useless, but it can be used to quickly pass text into a file (without first opening it!)

If I have **file.txt** in my current working directory, I can `echo` something into it, this way: `echo 'Hey There' > file.txt`. But using just one greater than sign **>** will replace all the text inside the file with **Hey There**.

To add or append to the end of the file do it this way: `echo 'append this son' file.txt' >> file.txt` 

### `nano` - a simple command line text editor

```bash
 
 nano <file>

 ```

Another way to edit a text file is to use nano.

Nano is a simple command-line text editor. It will open a file inside your terminal for you to edit it. `nano newFile.txt`

If the file exists it will open it inside nano, if not it will create a new file and open it inside nano.

To exit nano, look at the guide at the bottom. Press ctrl X. Then y to save change or n to not save. if you save you can rename the file or keep the same name. Press enter to keep the same name.

### `vim` - an advanced text editor

```bash

 vim <file>

```

One final way to create and edit text files is using Vim.

Vim is an advanced command-line text editor. It allows you to do everything inside a text editor without ever needing to touch a mouse. 

The problem with Vim is you can't use it unless someone tells you how!

That's why most people's first encounter with Vim, myself included, is getting stuck and not being able to exit!!

Vim needs its own intro so, for now, just use `open`, or `nano` and in the future, we can dive into Vim.

To exit Vim, press **ESC**, then write `:q!`, then press **return**, and you'll safely return to the terminal.

## 7. Customize {#cust}

Hang in there we're almost done!

I'll give you 2 ways to start customizing your command line XP. Off course, there's a lot more that can be done when it comes to customization, which we'll explore later. But this is just a start.

### `alias` - make a command shortcut

```bash

 $ alias <aliasName>='<command>'

```

The first thing you can do to customize your terminal XP, is to create aliases.

An alias is just a shortcut to long commands that you repeatedly use.

Here's an example of an alias I use; I write `lsg` to execute the command `ls -GhalS`. I set it this way; `alias lsg='ls -GhalS'`

You can also use aliases to `cd`, change directory (head to), and your most-used folders. For example: `alias myFolder='cd ~/Documents/myFolder`.

Typing an alias directly into the terminal will set it only for this session. Once this terminal window is closed, the alias will be gone! 

To make an alias permanent you need to add it to a file that manages the settings of your terminal. This filename depends on which shell you use, most probably your system will be using the **bash** shell, or if you have a new mac it will be **zsh**.

For **bash** open the file `~/.bashrc` using open or nano and add the alias to an empty line. For `zsh`: `open ~/.zshrc` and add your alias. These are hidden files inside your home **~** directory. 

After you add your alias to the `~/.bashrc` file, you need to restart the terminal for it to start working or write the command `source ~/.bashrc` to reload the terminal's settings from it.

If you want a list of all the aliases you have currently set. You can just write the command `alias`. This would be useful if you forgot what aliases you've set.


### `ps1='$ '` - prompt variable

And finally, if you want to customize the look of your prompt, you can edit the value of the variable **ps1** in the `~/.bashrc` file.

I prefer a minimal look with only the prompt.

If you want a minimal and clean prompt to add this `ps1='$ '` , in an empty line, to your `~/.bashrc`  Or `~/.zshrc` file

You need to `source ~/.bashrc` for this to take effect or start a new terminal tab.

## 8. What's next? Command Line Resources {#next}

Some resources that can help you learn more about using the command line.

### Command Line Cheatsheets

There is no need to memorize any command.

Understand what a command does, when you get introduced to it, and how it works, then choose a cheat sheet to get back to when you forget it. Or even better, make your own cheat sheet, with your favorite commands.

[Here's my cheatsheet](/dev/command-line-cheat-sheet/){:target="_blank"}

There is also a [cheatsheet by Codecademy](https://www.codecademy.com/learn/learn-the-command-line/modules/learn-the-command-line-navigation/cheatsheet){:target="_blank" rel="noreferrer"}, if you don't like how I structured my cheatsheet.

Or, just look up other Command-line cheatsheets online, and find one you like.

### Books To Self Study The Command Line

#### The Linux commands handbook by Flavio.

<a href="https://flaviocopes.com/page/linux-commands-handbook/" target="_blank" rel="noreferrer">
	<img alt="The Linux Commands Handbook, by Flavio" src="/assets/i/flavioBook.jpeg" style="max-width:20%;height:auto;">
</a>

This is a short book of commands and quick explanations, that the author thinks are used by shell users 80% of the time.

#### The Linux command line Book by William Shots  

<a href="https://www.linuxcommand.org/tlcl.php" target="_blank" rel="noreferrer">
	<img alt="The Linux Command Line Book, by William shotts" src="/assets/i/wsbook.png" style="max-width:20%;height:auto;">
</a>

A very recommended book that dives deep into the command line and that is suited for beginners.

### Online Class

#### The Missing Semester of Your CS Education, a class by MIT.

This class is a part of the [Open source society Uni](https://github.com/ossu/computer-science){:target="_blank" rel="noreferrer"}'s path to a free self taught education in computer science. 

### Tune in

I will continue to explore the command line on my website: [mstflotfy.com](https://mstflotfy.com/){:target="_blank" rel="noreferrer"}, and YT channel: [mstflotfy - indieDev](https://www.youtube.com/c/mstflotfyindieDev){:target="_blank" rel="noreferrer"} . I'll explore commands that used to confuse me, shell scripts, and vim. I will also explore other Dev subjects, as well as Ui and Ux Design. 