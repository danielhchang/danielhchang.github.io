---
title: Learning Jekyll
description: Personal Notes on using jekyll.
author: Daniel Chang
---

Static sites don't have any server-side processing and no database.  They have benefits of being faster and cheaper.  

Created using
```
$ gem install jekyll bundler
$ jekyll new demosite
$ cd demosite
$ bundle exec jekyll serve (starts the server on localhost:4000)

$ bundle show minima # (finds the minima theme directory)
```
Delete theme from `_config.yml` and from `Gemfile`
