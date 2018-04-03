---
layout: post
section-type: post
title: Run your Jekyll site locally using Docker
category: tech
tags: [ 'tutorial', 'docker', 'devops' ]
---
I recently dealed with [GitHub Pages](https://pages.github.com/) and [Jekyll](https://jekyllrb.com/) to build this site and since I usually work on my Windows 10 computer, I faced a lot of problem configuring Jekyll to test the site locally on my pc, because the OS is not fully supported by this Ruby project.

I have been dealing with a lot of errors also following the [official installation guide for Windows](https://jekyllrb.com/docs/windows/) then I considered that I never used Ruby and gem before and probably I will use it just for my site, so why install Ruby jin my machine ust to build a site with Jekyll?!?

I switched to [Docker](https://www.docker.com/) and everythings figure out! Thanks to [Docker for Windows](https://docs.docker.com/docker-for-windows/) you will be able to run linux-based images on a Windows system and it isn't a custom installation just for this site because you can use Docker for a lot of different purposes.

Now I'm going to describe you the solution I used and you will able to understand how easy it is.

### Requirements:
* Windows 10 Pro 64 bit (1607 Anniversary Update, Build 14393 or later)
* Hyper-V enabled 
* Docker for Windows

First of all we need to pull the `Jekyll image` from [Docker Hub](https://hub.docker.com/).

```
docker pull jekyll/jekyll
```

Now we have the image on our machine and we just need to run it mounting our Jekyll project's folder in `/srv/jekyll` container's directory.
The following command will build the site and write it in your disk.

```
docker run --rm --volume="<jekyll_project_direcotry>":/srv/jekyll -it jekyll/jekyll jekyll build
```

At the end we can serve the site using the same container, taking care to bind also a local port to the 4000 port of the container.
Here is the command you can use:

```
docker run --rm -p 4000:4000 --volume="<jekyll_project_direcotry>":/srv/jekyll -it jekyll/jekyll jekyll serve --force-polling
```

And you will be able to reach your site at [localhost:4000](http://localhost:4000)!

![jekyll running](/img/blog/jekyll-running.jpg)

This approach of course can work also on unix and macOS systems, thanks to the Docker abstraction layer.

### Conclusion
If you want to dev/test locally a Jekyll site without any additional compiler installed and without installing Ruby, RubyGem, ... and Jekyll on your host OS and you want to be as quick as possible to start.
You can use the steps above to use official Jekyll's Docker Image and have your site up and running in just a few minutes. 
Docker container speed up your configuration process!

I explained this configuration in a windows system but it's work also on Linux (or macOS - depending on the Docker's requirements) .

Thanks for reading! And share the post if you like it!