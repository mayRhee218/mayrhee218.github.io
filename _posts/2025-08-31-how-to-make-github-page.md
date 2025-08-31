---
layout: post
title: How to make Github page (Jekyll)
date: 2025-08-31 16:00:00 +/-1000
categories: [Projects(2025), Github Page(Jekyll)]
tags: [github_page, jekyll]     # TAG names should always be lowercase
author: mayRhee
---

I wanted to make the blog that I could write my learning outcomes, projects, book reviews in English.
Since I couldn't find good platform(Medium was the best, but it charges) so I decided to make own blog.

## Step1: Installing Ruby and Jekyll
If you want to use Jekyll for making github pages, you have to install ruby and jekyll.
Here's the link for it. 
You just follow the instruction.

[Jekyll installation](https://jekyllrb.com/docs/installation/macos/)

The error I got was even I installed 3.4.1 version with `ruby-install ruby 3.4.1`
when I checked the version with below command, I always saw my ruby's version is 2.6.0.

```
ruby -v
```

And it solved after I installed the ruby version manager.
```

brew install rbenv ruby-build
rbenv init

rbenv install 3.2.2

rbenv global 3.2.2   # set the default Ruby version for this machine (simpler)
rbenv local 3.2.2    # set the Ruby version for this directory 

ruby -v

```

[StackOverFlow: Installed latest ruby on mac but still showing old in terminal](https://stackoverflow.com/questions/76938956/installed-latest-ruby-on-mac-but-still-showing-old-in-terminal)

## Step2: Find the jekyll gibhub template you like

After I installed the ruby and Jekyll, I followed below link's instruction to make the blog.
[Jekyll을 이용해 GitHub에 블로그 만들기 (1)](https://jetalog.net/86)

It is usefull that I could make the basic jekyll github page like below.
![basic jekyll blog](/assets/img/pages/2025-08-31/basic-jekyll-blog.png)

However, I got trouble when I tried to adjust the theme that I like in my initial github page repository.
(Like build failure because of the Gemfile.lock)

So I recommend to find the github template you're using first and fork it and change the repository name as `<username>.github.io`.
Some repository provides this "Use this template" button. I used it. 

![Use this template](/assets/img/pages/2025-08-31/chirpy-starter.png) _The them that I chose: [Chirpy-Starter](https://github.com/cotes2020/chirpy-starter)_

## Step3 : Change github deploy as github actions

Go to your github page repository's 'Settings > Pages' and Change 'Build and Deployment' source as Github Actions. 

![github-actions](/assets/img/pages/2025-08-31/github-actions.png)

## Step4: Write the post
For writing the post or change the style, the ways are different depending on the template.
For me, since I used this [chirpy template](https://github.com/cotes2020/jekyll-theme-chirpy), I refered the document of it.

[Writing a New Post](https://chirpy.cotes.page/posts/write-a-new-post/#images)

## Step5: Finished

Now this is my blog and I could write the post and code