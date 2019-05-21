---
title: Learning Jekyll
description: Personal Notes on using jekyll.
author: Daniel Chang
---

# {{ page.title }}
## {{ page.description }}

I came across [Jekyll](http://jekyllrb.com/) when I started learning to use git and github.com.  [GitHub Pages](https://pages.github.com/), a service that provides free static-site hosting from a github.com repository.   This gives users the ability to publish a site within the `*.github.io` domain.  

What is a static site?  Most popular websites are powered by feature-rich content management systems that incorporate server-side technologies like perl and php.  In contrast, static sites don't have any server-side processing and no database.  They have benefits of being faster and cheaper.  

===
# Getting Started

## Installing Jekyll
```
$ gem install jekyll bundler
```
## Creating the scaffolds for a new site, "demosite"
```
$ jekyll new demosite
$ cd demosite
$ bundle exec jekyll serve (starts the server on localhost:4000)
```
You're left with a directory structure that looks like this:
```
.
├── 404.html
├── Gemfile
├── Gemfile.lock
├── _config.yml
├── _posts
│   └── 2019-05-21-welcome-to-jekyll.markdown
├── about.md
└── index.md
```

## Removing the default theme
```
$ bundle show minima # (finds the minima theme directory)
Delete theme from `_config.yml` and from `Gemfile`
```
===
# Output vs Tags

An output statement is a set of double curly brackets containing an expression; when the template is rendered, it gets replaced with the value of that expression.

A tag uses a set of open (and close) curly bracket and percent sign.  They are use for logic, such as a set of if / elsif / else / endif.  Another example is the for loop.  

## For Loop
```
{% for item in array %}
    {{ item }}
{% endfor %}
```

## Front Matter

Files that have YAML Front Matter will be processed by Jekyll.  Front Matter is identified with the content between the triple-dashed lines.  You can set both default and custom variables.
```
---
layout: default
title: great web agency
---
```

## Include
```
{% raw %}
    {% include home-slider.html %}
    {% include service.html%}
    {% include call-to-action.html %}
    {% include testimonial.html %}
{% endraw %}
```

===
# Resources

* [Official Jekyll Site](https://jekyllrb.com/)
* Udemy - [Jana Bergant](https://www.udemy.com/user/jana-bergant/) [Jekyll: make fast, secure static sites and blogs with Jekyll](https://www.udemy.com/static-website-generator-fast-secure-sites-blogs-with-jekyll)
* [Liquid for Designers](https://github.com/Shopify/liquid/wiki/Liquid-for-Designers)
* [Liquid Cheat Sheet](https://www.shopify.com/partners/shopify-cheat-sheet)
