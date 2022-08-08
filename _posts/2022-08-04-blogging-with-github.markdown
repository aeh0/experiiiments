---
layout: post
title: "Blogging with GitHub Pages and Jekyll"
author: "Alison Harvey"
date: 2022-08-04
---
The first thing I wanted to do when I started the Fellowship was set up a blog. Writing is how I plan, how I reflect, how I unpick problems and think my way around them. I'd heard a lot about static site generators, and something called Jekyll, as an alternative to a traditional CMS like Wordpress. It's one of the things I was hoping I would finally have time to explore once the project started - especially given its focus on minimal computing. 

Tom Preston-Werner created Jekyll for people that want to ['blog like a hacker'](https://tom.preston-werner.com/2008/11/17/blogging-like-a-hacker.html). Dash off your thoughts in markdown, pass posts through simple templates, and generate a complete static website, which is freely hosted, version-controlled, and served by GitHub Pages. What's not to like?!

Jeykll is beautifully simple - and with no superfluous functionality or features, and no clunky database, it's blisteringly fast. There's no advertising, branding, or logos. It offers complete control over design, allowing you to create your own theme or customise an uncomplicated base theme, which is great if you're starting out learning about html and css. And yes, it's free!
<!--more--> 
My first stop was [GitHub Skills](https://github.com/skills), where I worked through their 'first day' courses. The course on [GitHub Pages](https://github.com/skills/github-pages) got me up and running in no time - I made a blog in a matter of minutes. But I had no real sense of *how* I'd done it, or what any of it meant, so I headed to YouTube in search of something a little more in depth.

I highly recommend this series of videos by [Mike Dane](https://www.youtube.com/playlist?list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB), which walk you slowly through every single stage of the set up in a very accessible way.

Here's a summary of what you'll need, and proof that you can set up a free, unbranded blog with just a dozen lines of code. 

* Download [Ruby](https://rubyinstaller.org/downloads/) and install Jekyll (instructions for [Mac](https://www.youtube.com/watch?v=WhrU9m82Wm8&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=2) and [Windows] (https://www.youtube.com/watch?v=LfP7Y9Ja6Qc&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=3) are in the videos), plus [Git Bash](https://gitforwindows.org/), and a text editor, e.g. [Visual Studio Code](https://code.visualstudio.com/Download) 
* [Set up a GitHub account](https://docs.github.com/en/get-started/signing-up-for-github/signing-up-for-a-new-github-account) and create a [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)
* Open the command line.
* Type the following commands
```
dir [this lists the contents of the current directory]
cd [name of folder where you want to store your blog - choose from the list you just generated - I used cd Documents]
jekyll new [name of blog/site]
cd [name of blog/site]
bundle add webrick
bundle exec jekyll serve
```
* Go to GitHub and set up a new repository, with the name of your blog
* Go to Windows Explorer or equivalent, and go and look at your blog files! Open the config.yml, and enter the name of your repository under 'baseurl'. Save the file.
* Open Git Bash
```
cd [blog folder]
git init
git checkout –b gh-pages
git add .
git commit –m "load files"
git remote add origin https://github.com/[username]/[blog name].git
git push origin gh-pages
```
* Paste in your personal access token when prompted.
* Go to https://[username].github.io/[blogname] and admire your new blog!

Mike Dane's videos explain what to do next, such as how to write post and new pages in markdown. You'll save these files in your local folder, and when you're ready to publish, repeat the Git Bash code block above, from... 
```
git add
```
...onwards. Look at you - blogging like a hacker!

I installed GitHub Desktop which removes the stage of pushing files via Git Bash, and needing to keep my personal access code on hand, but this is optional.

I also had a dig around in my local Ruby folder (C:\Ruby31-x64\lib\ruby\gems\3.1.0\gems\minima-2.5.1), and copied the _includes, _layouts, _sass, and _assets folders. I opened the config.yml file and put a hash in front of the theme:
```
#theme: minima
```
This has allowed me to override the default theme that gets installed, and start to make minor, tentative changes. I wanted a short excerpt of each post to show on the home page, which required the following tweaks:
* Update config.yml:
```
show_excerpts: true
excerpt_separator: <!--more--> 
```
* Add 
```
<!--more-->
```
to every post, wherever I want the excerpt to stop. 
* Add the third line to the home layout to add a ‘continue reading’ prompt at the end of the excerpt
```
{%- if site.show_excerpts -%} 
    {{ post.excerpt }} 
    <a class="excerpt-post-link" href="{{ post.url | relative_url }}">Continue reading →</a> 
    {%- endif -%} 
```
Modifying the default minima theme really appeals to me, because I'm all about keeping things simple. I think it will help me learn as I go, and document any changes on the blog itself.

