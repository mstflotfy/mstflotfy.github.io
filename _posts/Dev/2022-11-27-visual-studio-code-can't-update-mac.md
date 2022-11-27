---
title: "[Solved] - Visual Studio Code Failed To Update On Mac"
layout: post
author: Mostafa Lotfy
section: Dev
permalink: /dev/vsc-cant-update-on-mac-fixed
---

## VS Code Failed To Install Volar Extension

My troubles started when I was following a Nuxt tutorial. I had a bad experience using Nuxt in VSCode on my Macbook. Contrary to the experience I had before (when I was using Vue on Ubuntu on a different computer). 

I was getting many errors for no apparent reason, and I wasn't getting code completion.

I realized that I'm using Vetur (the older vue language extension) extension, for VSCode, and the recommendation is to use Volar instead.

I tried to install Volar through VSCode, and it failed. Then I was prompted to install it manually. That failed too!

Then I got an error that Volar failed to install because Volar is not supported by my current VSCode version. So VSCode was not updated.

## VSCode Error: Cannot update while running on a read-only volume

I tried to update VSCode.

![VSCode settings icon clicked. A menu pops up with a "check for updates..." option, that is about to be clicked](/assets/i/vsc-wont-update-on-mac/vsc-check-for-updates.png)

But I got this error: 

`Cannot update while running on a read-only volume. The application is on a read-only volume. Please move the application and try again. If you're on macOS Sierra or later, you'll need to move the application out of the Downloads directory. See this link for more information.`

I was directed to [this post](https://github.com/microsoft/vscode/issues/7426#issuecomment-425093469){:target="_blank rel="noreferrer"}

![The link states that it's due to a well-known Squirell issue. And the workaround is to move the VSC app from the downloads to the Applications folder or run the code below](/assets/i/vsc-wont-update-on-mac/cannot-update-vscode-link.png)

I found others with the same problem on [this thread](https://github.com/Squirrel/Squirrel.Mac/issues/182){:target="_blank rel="noreferrer"}. Some people on this thread said that moving the VSC app out of the Apps folder and back again worked for them. Every time I tried to do that, the App did not move but created a shortcut.

But the following worked:

VSC was already in the Apps folder and not in the downloads folder, so I just needed to run the second command, where my app is currently installed (in the Applications folder inside the root directory)

```shell
$ cd /Applications
$ xattr -dr com.apple.quarantine "Visual Studio Code"
```


## Installing Volar worked after updating VSC

Next, I installed Volar, and it worked! And the experience of using Nuxt or Vue with Volar is much better than with Vetur. 

![Volar(Vue Language Features) installed and enabled in VSC](/assets/i/vsc-wont-update-on-mac/volar-installed-vsc.png)

P.S. You might need to disable Vetur to stop conflicts between it and Volar.

![Vetur disabled in VSCode](/assets/i/vsc-wont-update-on-mac/vetur-disabled-vsc.png)