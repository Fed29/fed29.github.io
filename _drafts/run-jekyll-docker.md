---
layout: post
section-type: post
title: Run your Jekyll site locally using Docker
category: tech
tags: [ 'tutorial', 'docker', 'devops' ]
---

Here you will be introduced to the Jekyll test environment based on Docker.

Requirements:


If you work on a Windows machine for sure you run in some problems related to gem and jekyll, that are not fully supported.

But also if you are working on linux (or MacOs) machine you needed to configure your machine, install packages and so on, just to test and debug your site before the production.

The docker container can speed up this process.

..................

I wanted to dev on a local jekyll site w/o having jekyll installed on my host OS
I wanted it to be as easy as possible to start

.... 

Keep in mind to not retro-dates the posts

```
docker pull jekyll/jekyll
```

```
docker run --rm --volume="D:\source\fed29.github.io":/srv/jekyll -it jekyll/jekyll jekyll build
```

```
docker run --rm -p 4000:4000 --volume="D:\source\fed29.github.io":/srv/jekyll -it jekyll/jekyll jekyll serve --force-polling
```



