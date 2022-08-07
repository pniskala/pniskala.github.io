---
title: "Learning by doing: Setting up a website with Hugo and GitHub Pages"
date: 2022-07-18T21:43:09+03:00
draft: false
categories:
- Development
- Web
tags:
- development
- hugo
- github
- web
---

I just set up this website with GitHub Pages and Hugo so why not share that experience on that very website? It only makes sense!

## Somewhat irrelevant background information

I have tried a variety of blogging platforms (e.g. Wordpress) in the past but I never got around to creating or hosting a website myself. Doing something like that sounded interesting for learning purposes, so why not try it out?

Well, to be honest, I am not really "creating" the website myself now either because I ended up using Hugo, nor am I actually hosting it myself as I opted for using GitHub Pages. I did play around with e.g Bootstrap and investigated hosting with AWS S3 but then again the sweet combination of Hugo and GitHub sounded too easy and cost effective (FREE!) to pass up.

Besides learning by doing, the main use cases for my website are twofold:
- Maybe it's too early 2000s, but I am fond of having a homepage besides all the social media sites, sort of like a business card.
- Having a platform to share my thoughts on a variety of topics. Again, maybe this is a bit old-fashioned and reflects me growing up in the world where everybody needed to have a blog.

My understanding was that the combination of Hugo and GitHub Pages should be more than enough for this purpose.

## Step 1: Setting up a repository for your website

As with any software project, it makes sense to use version control. Git is the natural choice here, and if you are going to use GitHub pages, you need to have a GitHub account as well. 

If you are not familiar with either of these, GitHub has good [introductory materials](https://docs.github.com/en/get-started/onboarding/getting-started-with-your-github-account) to get you started.

For the more experienced developers, the only real trick here is the name of the repository: for GitHub Pages to work, your repository needs to be named USERNAME.github.io, where you can naturally replace USERNAME with your actual GitHub username.

## Step 2: Creating the website with Hugo

[Hugo](https://gohugo.io/) is an open-source static website generator written in Golang. There are plenty of similar solutions, and to be completely honest, I did not have very specific reasons for choosing Hugo over e.g. [Jekyll](https://jekyllrb.com/) besides liking the software's own website and the themes on display.

To me the main point of using a static website generator like Hugo is the combination of ease-of-use and flexibility. Setting it up and adding new posts is easy but at the same time there's room for tuning and tinkering if you want to go deeper. And because it is open-source, it is also free. I acknowledge that a Content Managing System or a platform like Wordpress is easier to use for non-technical people but for a developer-spirited person tools like Hugo seem to work well.

Anyhow, getting started with Hugo was pretty easy by following the [Quick Start Quide](https://gohugo.io/getting-started/quick-start/):
- Install Hugo with `brew install hugo`.
- cd to the root of your repository, e.g `cd ~/Documents/pniskala.github.io/`.
- Type `hugo new site`.
- Choose a theme and add it to your repo with e.g `git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/hugo-PaperMod`.

In the end, I spent the most time looking at and trying out various [themes](https://themes.gohugo.io/). There are plenty of good looking ones but for me the usability and documentation are important as well. Based on a sample of few themes, the complex configuration files can make it cumbersome to figure out some of the simple things like how to change the title of the landing page. Well, at least I got some experience working with TOML files that [will get a standard library support with Python 3.11](https://realpython.com/python311-tomllib/).

I opted for the [PaperMod theme](https://themes.gohugo.io/themes/hugo-papermod/) but I will have to see how well it works if and when I start actually developing the website further. At least switching themes is a breeze with a simple website, so better get started with a Minimum Viable Product mentality rather than get stuck in polishing details.

There's typically some documentation in the demos of the themes but it also makes sense to check either the config files for the theme repositories (typically `exampleSite/config.toml`) or have a peek at the config file e.g. [at the repository of this website](https://github.com/pniskala/pniskala.github.io) to get a good starting point. Just be prepared that setting up the theme to your liking may take some time. 

## Step 3: Deploying your website with GitHub Pages

GitHub offers free hosting of static websites with their [GitHub Pages](https://pages.github.com/) solution. As a default, the website will have the URL https://USERNAME.github.io but you can also use a custom domain if you have one available.

There are two ways to get your website out there:
- Build your website manually locally and let GitHub Actions deploy the built website.
- Implement the end-to-end workflow in GitHub Actions and let it both build and deploy your website.

The configuration depends on which rout you end up taking. I would recommend using the latter option but that takes a little bit of extra effort with Hugo.

For those not familiar with the concept, GitHub Actions is similar to software like Jenkins: it allows you to create "workflows" or "pipelines", i.e. a sequence of tasks that is performed automatically when for example the code in a repository is updated. Typically this means building the code, running some tests on it, and deploying it somewhere so it can be used.

I have personally worked with Jenkins for Data Science workflows so having a glimpse of GitHub Actions was a nice bonus in this little project. 

### Option 1: Build manually

Executing `hugo -D` in your repository root will build the static website. However, it makes sense to configure first the output folder in your `config.toml` file by setting the `publishDir` parameter to `docs`. 

Then you need to go to the Settings tab of your repository on GitHub and select the Pages section. Select the right branch (most likely `main`) and the `docs` folder as the source for building and deploying the website.

After pushing your built website to the remote, it should be deployed and be accessible at https://USERNAME.github.io. If not, makes sense to check the Actions tab of your repository to find out if something went wrong with the deployment.

### Option 2: Building and deploying with GitHub Actions

It turns out [GitHub Pages supports natively Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/about-github-pages-and-jekyll) for building the website so I created some extra work for myself by choosing Hugo. Luckily it's not that difficult to achieve the same with other tools.

Apparently GitHub Pages always uses GitHub Actions to deploy the website but you can use a custom workflow for building it as well. This is exactly what we need to do.

The developers of Hugo of course have a nice [guide for setting up the Github Actions workflow](https://gohugo.io/hosting-and-deployment/hosting-on-github/). Basically you need to do two things:
- Add a workflow configuration file to your repository as `.github/workflows/gh-pages.yml`. You can find the configuration file in the guide.
- Go to the Settings tab of your repository on GitHub and select the Pages section. Select the `gh-pages` branch and the root folder as the source for building and deploying the website.

With this setup, the website should be built to the branch `gh-pages` and deployed automatically from there every time you push changes to your repository. If your website fails to update, it makes sense to check the Actions tab of your repository at GitHub. Red lights indicate something is going wrong and you should probably have a deep dive to debug the issue.

*Update 2022-08-07: GitHub Pages just launched a new feature that makes publishing your website easier with a variety of frameworks, including Hugo. Check it out [here](https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/).*

## Conclusion

That's all folks! 

With this setup, I can write write stuff with Markdown for the website, push it to the remote repository, and the stuff is magically appearing on the website. Oh what a world we live in.

Hopefully I did not at least confuse anyone more with my ramblings. Let's see where I end up going with this website or if it will end up at the graveyard with all those other cute hobby projects.