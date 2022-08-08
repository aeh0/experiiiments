---
layout: post
title: "Blogging with GitHub Pages and Jekyll"
author: "Alison Harvey"
date: 2022-08-04
---
As soon as I started the Fellowship, the first thing I wanted to do was start a blog. Writing is how I plan, how I reflect, how I unpick problems and think my way around them. I'd heard a lot about static site generators, and something called Jekyll, as an alternative to a traditional CMS like Wordpress. It's one of the things I was hoping I would finally have time to explore once the project started. 

Tom Preston-Werner created Jekyll to enable people to ['blog like a hacker'](https://tom.preston-werner.com/2008/11/17/blogging-like-a-hacker.html). Dash off your thoughts in markdown, pass posts through simple templates, and generate a complete static website, which is freely hosted, version-controlled, and served by GitHub Pages. What's not to like?!

Jeykll is beautifully simple - and with no superfluous functionality or features, and no clunky database, it's blisteringly fast. There's no advertising, branding, or logos. It offers complete control over design, allowing you to create your own theme or customise an uncomplicated base theme, which is great if you're starting out learning about html and css. And yes, it's free!
<!--more--> 
My first stop was [GitHub Skills](https://github.com/skills), where I worked through the 'first day' courses. The course on [GitHub Pages](https://github.com/skills/github-pages) got me up and running in no time - I made a blog in a matter of minutes. But I had no idea how I'd done it, or what any of it meant, so I headed to YouTube in search of something a little more in depth. 

I highly recommend this series of videos by [Mike Dane](https://www.youtube.com/playlist?list=PLLAZ4kZ9dFpOPV5C5Ay0pHaa0RJFhcmcB), which walk you slowly through every single stage of the set up in a very accessible way.

Here's a summary of what you'll need, and proof that you can host a free, unbranded blog with just a dozen lines of code. 

* Download and install Jekyll (instructions are in the videos), plus Git Bash, and a text editor, e.g. Visual Studio Code 
* [Set up a GitHub account](https://docs.github.com/en/get-started/signing-up-for-github/signing-up-for-a-new-github-account) and create a [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)
* Open the command line.
* Type the following commands in bold
```
dir [this lists the contents of the current directory]
cd [name of folder where you want to store your blog - I used cd Documents]
jekyll new [name of blog/site]
cd [name of blog/site]
bundle add webrick
bundle exec jekyll serve
```
* Go to GitHub and set up a new repository, with the name of your blog
* Go to Windows Explorer or equivalent, and go and look at your blog files! Open the config.yml, and enter the name of your repository under 'baseurl'. Save the file.
* Open Git Bash, and change directory (cd) into your blog folder
```
git init
git checkout –b gh-pages
git add .
git commit –m "load files"
git remote add origin https://github.com/[username]/[blog name].git
git push origin gh-pages
```
* Paste in your personal access token when prompted.
* Go to https://[username].github.io/[blogname] and admire your new blog!

Now you can write in markdown, saving posts in your local folder. When you're ready to publish, repeat the Git Bash stage above. Look at you - blogging like a hacker!