---
layout:		post
title:		Build a static blog with Jekyll and Github Pages
category:	misc
author:		Tiantian Li
---

Here are all you have to do to build a Jekyll blog. See? Simple.

```shell
# Prerequisites:
# Ruby, Jekyll, Bundler installed
# A empty github repository

# Under the PARENT FOLDER that will hold the website
$ git init <user>.github.io

# Initialize a Jekyll website
$ cd <user>.github.io
$ jekyll new --skip-bundle .

# Edit the Gemfile following the intructions inside
$ vim Gemfile

# Install the gems
$ bundle install

# Now the website is ready to go, serve it locally 🎉
$ bundle exec jekyll serve

# (Optional) If there are errors, try adding webrick dependency
$ bundle add webrick

# Just commit and push
# Note: the website can be deployed by 'publish from a branch' (legacy) or a custom Github Actions (beta)
$ git add .
$ git commit
$ git remote add origin https://github.com/OWNER/REPOSITORY.git
$ git push
```

Check out the following links for more detailed explanation:

[Install Jekyll](https://jekyllrb.com/docs/installation/)

[Configuring a publishing source for your GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

