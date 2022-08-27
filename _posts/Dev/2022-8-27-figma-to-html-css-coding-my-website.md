---
title: Figma to HTML & CSS - How I coded my first website
layout: post
author: Mostafa Lotfy
section: Dev
permalink: /design/figma-to-code-html-css
description:   
image: /assets/i/dev9/figma-to-code-responsive-website-html-css-jekyll-article-cover.png
---

In this article, I want to show you how I took a Figma design and turned it into a live website using HTML & CSS. And finally deployed it with Jekyll and GitHub pages.

I am documenting the lessons I come across while I work on building my own indie apps.

As an exercise to learn Figma, I redesigned my website. 

![a design of a mobile webpage inside Figma](/assets/i/dev9/figma-responsive-design-website-mobile-figma-to-code.png)

I implemented this Figma design into my website.

 ![Same design as above implemented with html and css and running live on my website mstflotfy.com](/assets/i/dev9/figma-to-code-html-css-mstflotfy-responsive-website-mobile.png)
    
You can see the [Figma design file here](https://www.figma.com/community/file/1051279558347794166){:target="_blank" rel="noreferrer"}, and if you're not already there, [you can visit the live website here](http://mstflotfy.com/).  

Also, here's a [GitHub repo of the HTML & CSS](https://github.com/mstflotfy/mstflotfy-redesign-exercise/tree/main){:target="_blank" rel="noreferrer"} as I plan a more deliberate remake of my website soon.

**This is not a step-by-step guide**, just documenting the main steps I took and the thought process. However, more practical lessons will be coming soon.
	
## Step 1 -- Designing An Entire Website In Figma

![Figma file for mstflotfy.com redesign with full pages and components](/assets/i/dev9/figma-file-full-design-and-components.png)

This is the starting point.

I have already gone through how I designed the website in 2 previous videos.

In [this first video](https://youtu.be/LTmHoRJLcuY){:target="_blank" rel="noreferrer"} I quickly went thought the general process, then in [the second](https://youtu.be/euXzyxr_d6A){:target="_blank" rel="noreferrer"}  you can find a step-by-step guide, starting from scratch.
 In brief: It is not an ideal well-thought start. It started as an exercise to practice making designs in Figma. Then I took it a bit further into a full redesign of my website. I heavily used Figma's auto-layout and components.

In this [Figma Community file](https://www.figma.com/community/file/1051279558347794166){:target="_blank" rel="noreferrer"}, you can find the final design.

![Figma community that can be duplicated](/assets/i/dev9/free-figma-community-file-full-design-and-prototype-for-personal-webiste.png)

As for responsiveness, I made three designs; for desktop, tablet, and mobile. Then I figured out the in-between sizes while I was coding.

In this case, I think this was good enough. In a previous video, I explored how to create a fully responsive design in Figma using breakpoints. You can have a look at it [here](https://youtu.be/3KUZ3o0ddcE){:target="_blank" rel="noreferrer"}.

So basically, I didn't start from scratch. I had a Figma file with components and pages.

## Step 2-- Prep The Figma File For Coding

![free figma community file. website design and design system in figma.](/assets/i/dev9/free-figma-file-personal-website-design-system.png)


I was itching to jump straight into code. 

But, I decided to first research how to go from Figma to code. 

I came across 2 keywords; **developer handover** and **design systems**. Those need to be explored on their own. But I decided to keep things simple.

Before I started, I wanted to make a basic design system and name components and elements consistently.

### Design System
I realized I had to think deliberately about many things, including typography, color, spacing between components, pages, and assets, ...

I already had most of those things somewhat in place. I had components for everything I used across the pages that I made. 

Yet, after a closer look, I found many inconsistencies, especially with color, typography, and spacing.

So I made a simple typography scale, then experimented and adjusted it a bit to fit the design.

Also, I limited the color palette. And tried to use it consistently across elements and pages.

Finally, I had to think of readability. I used [Adobe Color's Contrast Checker](https://color.adobe.com/create/color-contrast-analyzer){:target="_blank" rel="noreferrer"} to do this. This made me change the color slightly for some fonts and adjust the type scale to make sure smaller font sizes are readable.

![A screenshot of Adobe color's contrast checker](assets/i/dev9/adobe-color-contrast-tool-screenshot.png)

### Naming Components And Elements
I wanted to name components and elements in a consistent way across the design and code.

So instead of coming up with my own naming system, I decided to try BEM. 

[BEM](https://css-tricks.com/bem-101/){:target="_blank" rel="noreferrer"} (Block, Element, Modifier) is a naming convention for classes in HTML and CSS.

I think I didn't do the best job with naming. Generally, I treated components as blocks, the items inside components as elements, and component variants as modifiers.

For example, the header's default component will have a class **header**. The list of links inside it will be an element with a class **header__link-list**. And the header's mobile variant will have a class **header--mobile**.

While it might seem straightforward, sometimes there will be elements inside elements and other independent components inside your component. This opens the room for interpretation, and different people handle it differently. 

Again with naming, I wasn't consistent enough, so next time I need to think this through and do a cleaner job.

In this [Figma Community file](https://www.figma.com/community/file/1144516865792093918){:target="_blank" rel="noreferrer"}, you can find the final design after making the changes.

## Step 3--Turning the Figma design into HTML

I laid out the [HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started#what_is_html){:target="_blank" rel="noreferrer"} structure for each page, starting with the landing page and focusing only on the desktop design. 

Tried my best to use [semantic HTML](https://developer.mozilla.org/en-US/docs/Glossary/semantics#semantics_in_html){:target="_blank" rel="noreferrer"} and minimize the use of [divs](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/div){:target="_blank" rel="noreferrer"}, but of course, I sometimes had to resort to them.

Also, I tried to give elements class names matching the naming in the [Figma file](https://www.figma.com/community/file/1144516865792093918){:target="_blank" rel="noreferrer"}.

I laid out the HTML structure for all the pages then I moved to [CSS](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/What_is_CSS){:target="_blank" rel="noreferrer"}.

Using [Visual Studio Code](https://code.visualstudio.com/){:target="_blank" rel="noreferrer"} and installing the [live server extension](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer){:target="_blank" rel="noreferrer"}, I used a local server to see the live changes while I coded.

## Step 4-- Styling With CSS

I started by setting some [CSS variables](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties){:target="_blank" rel="noreferrer"}. 

![CSS variables applied to the root element](assets/i/dev9/css-variables-example.png)

I used the styles that I set in the [Figma file](https://www.figma.com/community/file/1144516865792093918){:target="_blank" rel="noreferrer"}.

![Text and color styles from the Figma design](assets/i/dev9/figma-text-color-styles.png)

Then I finished styling all the pages for the desktop design, intentionally ignoring responsiveness. 

After I finished, I added media queries to target different screen widths. 

I started targeting smaller screens, then I tackled larger screen sizes.

Mainly targeting elements using classes, I tried to minimize other selectors but sometimes had to resort to them.

I also used Figma's "Inspect panel", It's not a copy-and-paste solution, but it helped a lot.

![Figma's code inspector panel showing CSS code for the header design](assets/i/dev9/figma-code-inspector-panel-example.png)

Having the fonts set using rem instead of pixels helped make this easier.

I didn't use any JavaScript code. 

I jumped back and forth between HTML and CSS and looked up some CSS tricks to show and hide elements using CSS only.

Finally, I had yet another prototype. But in HTML and CSS instead of Figma. 

To actually deploy the website, I had to find a way to integrate this HTML and CSS into my actual Jekyll website.

## Step 5-- Integrating The HTML & CSS into Jekyll

![Jekyll static website generator web page screenshot](assets/i/dev9/jekyll-landing-page.png)

[Jekyll](https://jekyllrb.com/){:target="_blank" rel="noreferrer"} is a static site generator. I use Jekyll so that I can write my articles in [Markdown](https://en.wikipedia.org/wiki/Markdown){:target="_blank" rel="noreferrer"}, push them to GitHub, and the changes would go live.

My website was already running using the [Jekyll minima theme](https://github.com/jekyll/minima){:target="_blank" rel="noreferrer"}, which I had [cloned](https://github.com/git-guides/git-clone){:target="_blank" rel="noreferrer"} and deployed on [GitHub pages](https://pages.github.com/){:target="_blank" rel="noreferrer"} (where I host my website).

I already knew how Jekyll generally works. I didn't go too deep into it, and I don't want to. I just needed to figure out how to place my HTML and CSS with minimal changes.

## Step 6-- Deploy & Test

While setting things up in Jekyll, I tested locally on many different browsers.

![Testing my code in browser for many devices](assets/i/dev9/testing-website-locally.png)

When I got decent results, I committed the changes and pushed them to the GitHub repo hosted on GitHub pages. In a couple of minutes, it was up and running.

Next, I tested the website on every device I could find.

## Step 7-- Fix Issues

I didn't find many issues as I already tested locally first. But trying the website on different browsers on different devices brought up new problems.

I fixed some issues that can't be ignored, but the things that could wait, I noted and decided to fix things incrementally when I have the energy for them. 

Every time I visit the website, I keep making little improvements testing locally, and then pushing to the GitHub repo.

## Other articles you might want to read
-   [How To Start A Blog](/dev/how-to-start-a-blog/)
-   [An Introduction To The Command Line](/dev/command-line-very-beginner/)