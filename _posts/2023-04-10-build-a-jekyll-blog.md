---
layout: post
title: Build a static blog with Jekyll and GitHub Pages
category: misc
author: Tiantian Li
---

Anyone can build a Jekyll blog in 5 minutes.

## Prerequisites

- Ruby
- Jekyll
- Bundler
- A empty GitHub repository

## Instructions

Here are all you have to do to build a Jekyll blog.

```shell
# Under the PARENT FOLDER that will hold the website
$ git init <user>.github.io

# Initialize a Jekyll website
$ cd <user>.github.io
$ jekyll new --skip-bundle .

# Example: https://github.com/Arcohol/arcohol.github.io/blob/master/Gemfile
$ vim Gemfile

# Install the gems
$ bundle install

# Serve the website locally for debugging
$ bundle exec jekyll serve

# Commit and push
# Note: the website can be deployed by 'publish from a branch' (legacy) or a custom Github Actions (beta)
$ git add .
$ git commit
$ git remote add origin https://github.com/<OWNER>/<REPOSITORY>.git
$ git push
```

## References

- [Install Jekyll](https://jekyllrb.com/docs/installation/)
- [Configuring a publishing source for your GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)
