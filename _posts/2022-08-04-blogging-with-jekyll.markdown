---
layout: post
title: "Blogging with Jekyll"
author: "Alison Harvey"
date: 2022-08-04
---
The first thing I wanted to do when I started the Fellowship was set up a blog. Writing is how I plan, how I reflect, how I unpick problems and think my way around them. I'd heard a lot about static site generators, and something called Jekyll, as an alternative to a traditional CMS like Wordpress. It's one of the things I was hoping I would finally have time to explore once the project started - especially given its focus on minimal computing.

Tom Preston-Werner created Jekyll for people that want to ['blog like a hacker'](https://tom.preston-werner.com/2008/11/17/blogging-like-a-hacker.html). Dash off my thoughts in markdown, pass posts through simple templates, and generate a complete static website, which is secure, freely hosted, version-controlled, and served by GitHub Pages. What's not to like?! I didn't require much from a blog - just a place to record thoughts in a tidy, systematic way. The idea of being able to start simple, but modify any aspect of appearance or configuration, appealed to me, as someone who has always learned by fiddling with the controls.
<!--more-->
Jeykll is beautifully simple - and with no superfluous functionality or features, and no clunky database, it's blisteringly fast. It's clean and uncluttered - no advertising, branding, or logos. Most importantly for me, it offers complete control over design, allowing me to create my own theme or customise from a simple base theme, which is great for anyone just starting out learning about html and css. And yes, it's free!

My first stop was [GitHub Skills](https://github.com/skills), where I worked through their 'first day' courses. The course on [GitHub Pages](https://github.com/skills/github-pages) got me up and running in no time - I made a blog in a matter of minutes. But at the end, I had no real sense of *how* I'd done it, or what any of it meant, so I headed to YouTube in search of something a little more in depth.

I highly recommend this series of videos by [Mike Dane](https://www.youtube.com/playlist?list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB), which walk you slowly through every single stage of the set up in a very accessible way.

Here's a summary of what's needed, and proof that anyone can set up a free, unbranded blog with just a dozen lines of code. 

* Download [Ruby](https://rubyinstaller.org/downloads/) and install Jekyll (instructions for [Mac](https://www.youtube.com/watch?v=WhrU9m82Wm8&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=2) and [Windows] (https://www.youtube.com/watch?v=LfP7Y9Ja6Qc&list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB&index=3) are in the videos), plus [Git Bash](https://gitforwindows.org/), and a text editor, e.g. [Visual Studio Code](https://code.visualstudio.com/Download) 
* [Set up a GitHub account](https://docs.github.com/en/get-started/signing-up-for-github/signing-up-for-a-new-github-account) and create a [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)
* Open the command line.
* Type the following commands
```
cd [name of folder where you want to store your blog]
jekyll new [blog name]
cd [blog name]
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

The tutorials in Mike Dane's [playlist](https://www.youtube.com/playlist?list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB) explain what to do next, such as how to write posts and new pages in markdown. These files are saved in a local folder, and when ready to publish changes, run a few commands in Git Bash:
```
git add . 
git commit –m "[comment here]" 
git push origin gh-pages 
```
You can avoid this step by installing GitHub Desktop, which also avoids to need to keep a personal access code on hand, but this is optional.

I can never resist a few modifications, and learned the following means of overriding the default theme that gets installed (minima). In my local Ruby folder, C:\Ruby31-x64\lib\ruby\gems\3.1.0\gems\minima-2.5.1, I copied the _includes, _layouts, _sass, and _assets folders, and pasted them into my blog folder. I opened the config.yml file and put a hash in front of the theme, cancelling it out:
```
#theme: minima
```
Now I could start to make minor, tentative changes. I wanted a short excerpt of each post to show on the home page. This required the following tweaks:
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
Modifying the default minima theme gradually really appeals to me, because I'm all about keeping things simple. I think it will help me learn as I go, and be able to document any changes on the blog itself.

The next step for me is to investigate some [issues I've been having recently with our implementation of the Universal Viewer](https://aeh0.github.io/experiiiments/2022/08/08/universal-viewer.html). It's the sort of problem I need to *show* rather than describe, and I think that the blog will be the perfect place to display the results of the tests I've been running, and share the outputs with colleagues who may be able to help me get to the bottom of it.