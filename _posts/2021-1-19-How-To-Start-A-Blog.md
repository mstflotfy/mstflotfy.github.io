---
title: How To Start A Blog
layout: post
sitemap: false
permalink: /dev/how-to-start-a-blog/
layout: redirected
redirect_to: https://dev.mstflotfy.com/how-to-start-a-blog/
---

A couple of weeks before I wrote this post, I had no idea how to start a blog or any website.

I had many questions, and after searching online, they only multiplied.

<br>

> Should I use WordPress? Should I use a site builder like Wix or Squarespace? Should I learn web Dev? How do I host my blog? Should I first start blogging on Medium? Should I use GitHub Pages free hosting? What is a static website? What is Jekyll? Should I consider other static site generators than Jekyll? Do I need to understand and think about SEO before I start? Where should I get a domain name? Should I go with .com or something else? How do I connect the domain name to my website?

<br>

These are some of the questions that overwhelmed me.

I overthought it.
The best thing to do is choose a path that makes sense, start immediately, and figure things as you go.
No matter how long you think and analyze, eventually, you will find a better way to do things. The time spent postponing is wasted.

**To start, you only need three things**
- Build the blog.
- Host it on a server.
- Buy a domain name and connect it to your website.

## **Buying A Domain Name**

First, let's get the domain name out of the way.

- The domain name is the address of your blog. [mstflotfy.com](https://mstflotfy.com/) is the domain name of this blog.

- You more rent a domain name than buy it. It’s yours for the years you have paid for, then you need to renew if you do not, it will be up for sale, and others will be able to buy it.

- It does not matter where you buy it. Just find a well-known site that has good buying and renewal prices. I checked [Google Domains](https://domains.google/) and [NameCheap](https://www.namecheap.com/), but there are many other options.

- The domain name extension doesn’t matter much. Although it’s best to go with .com as it is the better-known option and easy to remember. Also, some weird extensions might be considered spammy. If .com is not available, go with any other familiar option.

- When registering, do not buy any extras except WhoisGuard. Most of the time, your hosting service will provide an SSL certificate. If it doesn’t you’ll need to buy it as well. WhoisGuard protects your personal information from spammers. An SSL certificate is required to have an HTTPS connection. HTTPS provides an encrypted, thus more secure website connection. If you do not have it, people and search engines will not trust your website. You know it’s there by seeing the little lock sign beside the URL in the address bar of your browser.

- Connecting the domain name to your website is not complicated. You'll just point your host to your domain name and then point your DNS to your host and its URLs. Your host and domain name service should have guides on how to do this. Or you can just google how to do it for your specific services.


I ended up buying the domain name from NameCheap. It had a good price with WhoisGuard included.

Do not overthink where to buy it as you can transfer next year. I am considering transferring my domain name to [Cloudflare's registrar](https://www.cloudflare.com/products/registrar/) next year. They offer at cost renewal prices and other security services.

## **Building And Hosting A Blog**

Choosing a host and building the site are somewhat connected, so I'll address them together.

**What is web hosting?**<br>
To simplify, a host is a computer that is always connected to the internet. You upload your site to the host, and when someone visits your site and requests to access a page, the host serves it to them.

There are many ways to build a website. Let's narrow it down to three that anyone starting a blog should consider. I ordered those by popularity.

#### **Three ways to build and host a blog**
- Host the site on a shared hosting service, like Bluehost, and build it with [WordPress](https://wordpress.org/download/).
- Build and host the site on a drag and drop platform like [Wix](https://www.wix.com/), or [Squarespace](https://www.squarespace.com/).
- Build the blog with a static site generator like [Jekyll](https://jekyllrb.com/) and host it on a free static hosting service like [GitHub Pages](https://pages.github.com/).

<br>

#### **`1 Shared hosting and WordPress`**
- **What is WordPress**?
  - WordPress is a free [CMS](https://en.wikipedia.org/wiki/Content_management_system) (content management system) software. It allows you to manage the content of your site without dealing with code. WordPress is the first option I considered, and it seems to be the most popular way to build a website.
- **What are the pros of WordPress?**
  - It has many [plugins](https://en.wikipedia.org/wiki/WordPress#Plugins). A plugin is a bit of code that can be uploaded to your website to extend its functionality without writing the code yourself.
  - It has many themes. You can start immediately with your website without much knowledge of coding or design.
- **What are the cons of WordPress?**
  - It could get bloated and slow.
  - It has a learning curve.
  - You might need to tweak the code of the themes and plugins to get them to work.
  - It’s [not the most secure](https://www.cloudways.com/blog/wordpress-security-issues-and-fixes/) option.
- **What is shared hosting?**
  - [Shared hosting](https://en.wikipedia.org/wiki/Shared_web_hosting_service) is sharing a server with other websites to reduce the price.
- **What are the pros of shared hosting?**
  - The main benefit is the lower costs.
  - They make it easy to install and manage WordPress.
- **What are the cons of shared hosting?**
  - Since you share the server with other websites, if some site is popular or has a sudden surge of traffic, this could affect your website's performance.
  - It is hard to find an honest opinion about which host to choose. The shared hosting option I kept coming across is BlueHost, yet there are many other options. I am sure with deeper digging it can be found. You can move away from the hosting service after the year is over, so do not overthink it.
- **Why I did not build my blog with WordPress and shared hosting**
  - Even though WordPress is free, I would still have to invest in hosting. I'd like to keep my expenses to a minimum until the site grows.
  - There are ways to handle security vulnerabilities and bloatedness. But why not just find a solution that has better security and is more lean and efficient.

#### **`2 Drang & Drop Site Builders`**

When I got overwhelmed, I started thinking about drag and drop site builders. It became alluring to sign up, pay the money, and not worry about hosting or domain names, or learning curves.

- **What are the pros of site builders?**
  - The easiest option to use.
  - No knowledge of code or tinkering is needed.
  - Themes and plugins work without tweaking code.
  - Great looking site immediately.
- **Why I did not build my blog with drag and drop site builders**
  - They are even more expensive than shared hosting. I will invest in this site but not before it starts to grow.
  - I would be limited to their themes.
  - When I set out in a direction, I like to have multiple goals. I want to start a blog, but I also want to learn new strategic skills. Using Drag and Drop Site Builders, my learning will be minimal.

#### **`3 Free hosting for static websites`**

I finally stumbled on [GitHub Pages](https://pages.github.com/).

Github Pages has free hosting! But this free hosting is for static websites only.

A static website?
I had no idea what those were as well.

- **What is a static website?**
  - The typical definition is, just like the name implies, a website that displays pages that do not change. Pages that are the same to everyone, not customized to each visitor. It does not change when users interact with it.
  - Some argue that static websites are the future of the internet, and you could almost do everything with them.
  - Others argue that they are only useful for simple websites with no interaction whatsoever.
  - Wherever the truth lies, as a beginner it does not matter to me. It is an easy, simple, free way to start blogging and learning about web development.
- **What are the cons of a static website?**
  - Working with a text editor and the command line and the need to tinker with code will put off most people.
  - To add dynamic functionality like comments or contact forms, the beginner will have to resort to and depend on a third party, like Disqus.
- **What are the benefits of a static website?**
  - It is generally faster and more stable than WordPress.
  - More secure than other options.
  - Possibly improved SEO.
  - Static websites are Cheaper to host as they use fewer resources.
- **GitHub Pages**
  - [GitHub](https://github.com/) is a well-known website used by developers to store their projects online.
  - GitHub Pages is not the only service that provides free hosting for static websites. There are many other options, including GitLab Pages, Cloudflare Pages, and Netlify.
- **Static Site Generators**
  - Static site generators take your text files and turn them into a static website, that can be hosted on services like GitHub Pages.
  - Jekyll is the first static site generator I came across. But there are [many other static site generators](https://jamstack.org/generators/).
- **Why I built my blog with Jekyll and GitHub Pages**
  - I chose Jekyll as it allowed me to build a basic blog immediately by knowing the very basics of a few things. And those very basics would lead the way for more learning as I build up the site. Though it might be intimidating, once you get past the initial setup, the workflow is enviable. But to customize it, you need to learn more and tinker more.
  - This is a skill worth investing my time learning. The things I will learn can be transferred to other technologies and lead to many directions.
  - And of course, I can host my blog for free on GitHub Pages until the website starts growing.

To take this direction, you must be willing to get familiar with new subjects, including git, GitHub, Markdown, the command line, and Jekyll. And to customize your blog, you will need to learn Jekyll, not just get familiar with it.

## **Quick Recap**

  I chose to host my blog on GitHub Pages, I built the site with Jekyll, and I bought a .com domain name from Namecheap.

  Quick Reasons
  - GitHub Pages is free.
  - It is quick and easy to start with Jekyll.
  - .com is what most people are familiar with.
  - Namecheap had reasonable prices.

  Next year I might consider hosting on Cloudflare Pages or Netlify, sticking to Jekyll unless it becomes a pain, and migrating the domain name to Cloudflare.

  The purpose of this post is not to have an accurate and thorough understanding of the subject. But to get to the outcome quickly, with a simplified view, and a minimal investment of time, effort, and money. Building knowledge over time as needed.

  Those are not all the options out there, but the ones I considered.

  Whatever path you choose to take, do not waste your time overthinking. Pick a direction and start now and learn as you go. Then you will find the right fit for you.

## **Next Steps**
  If you do not mind learning new skills and saving money. Here is [A step by step guide to start a blog with Jekyll](/step-by-step-guide-start-blog-with-jekyll/).

  You will get familiar with the command-line, Jekyll, git & GitHub, and Markdown. You will build your blog or personal website and host it for free on GitHub Pages.

  There is no need to have a complete understanding of each subject. In time, you can dig deep when you need to.
