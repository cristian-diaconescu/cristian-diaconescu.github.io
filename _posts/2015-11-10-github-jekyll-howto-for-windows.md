---
layout: post
title: How to write and preview a Github Pages blog post locally on Windows
#excerpt_separator: <!-- more -->
categories: jekyll github-pages
comments: true
---
So you're editing a post on a blog hosted on Github Pages, but you'd like to preview your masterpiece-in-the-making on your own machine before bestowing it upon the whole world? This is a step-by-step tutorial to achieve that, with an emphasis on Windows.

[Github Pages](https://pages.github.com/) is a handy, free hosting provider for your blog. 

You can host one site per account, for your personal/organization blog, and also one site for each of your projects (repositories). [Go here](https://pages.github.com/) to create your site.


The address where the blog is available by default is `http://<yourGithubUser>.github.io`, although it supports pointing to your own domain, if you have one.

The blog is hosted right from the Github repo named `<yourGithubUser>.github.io`. When a new post is ready, you just `push` it and it's up there for the world to see.

But what about previewing the post while you are writing it? Github Pages uses [Jekyll](https://jekyllrb.com/) to compile a static image of your blog. It does this every time you commit changes. 

At a minimum, you could be editing the source files of your blog directly in Github, and the changes would be seen by refreshing your public site in the browser.

If you want local preview, you have some installing work ahead.

Here's the checklist:

- git client - I like [Git Extensions](https://gitextensions.github.io/) and _love_ the awesome [SmartGit](http://www.syntevo.com/smartgit/) (which is not free for commercial use) 
- Ruby
- Python
- Jekyll
- a Markdown split-pane editor - I'm using [MarkdownPad](http://markdownpad.com/)

I won't go into details about the git client or markdown editor - take your pick.

## Installing Ruby on Windows

Why? 'Cause Jekyll is written in Ruby.

There's a project named [Ruby Installer](http://rubyinstaller.org/) that caters exactly for getting a Ruby distribution up and running on Windows.

### The framework

 Download and install a recent version of Ruby ( >= 2.0)

  - pick the **32 bit** version to spare yourself some headaches.
  - By default this installs under `C:\Ruby22\`

### The native build chain

On the same Downloads page, find and download the corresponding **DevKit**.

Why? Jekyll has dependencies that need a native build chain in order to be installed.  
The instructions for installing the DevKit [are here](https://github.com/oneclick/rubyinstaller/wiki/Development-Kit). 

Here's the tl;dr version:

Extract the contents of the DevKit in a "permanent location", like `C:\Ruby22\DevKit\` 

Now open a command prompt at `C:\Ruby22\DevKit\` and run:

    ruby dk.rb init
    ruby dk.rb install

## Installing Python

Why? Because some of Jekyll's dependencies (like `Liquid`, the templating engine) require it.

If you don't have `python` installed and available in your `PATH`, you will get an error when trying to build or serve the site:

>  Liquid Exception: No such file or directory - python C:/Ruby22/lib/ruby/gems/2.2.0/gems/pygments.rb-0.6.3/lib/pygments/mentos.py in _posts/2015-11-10-welcome-to-jekyll.markdown

Download and install Python 2.7 (not 3.0 !) from here: [https://www.python.org/downloads/windows/](https://www.python.org/downloads/windows/)  
By default it installs under `C:\Python27\`

Now test it: open a command prompt and run:

    where python

If it's not found, add `C:\Python27\` to the `PATH` environment variable and try again (after closing and reopening the command prompt window).

## Installing Jekyll

With all the pre-requisites out of the way, we can now finally install _Jekyll_. ...or?

### This is not the Jekyll you're looking for
 
Don't just sprint ahead and install the default Jekyll gem (like I did)!

You can read the [official instructions](https://help.github.com/articles/using-jekyll-with-pages/#installing-jekyll) for installing the Github flavor of Jekyll.  
Or you can keep reading the compact version here. 

The latest version of Jekyll at the time of writing is 3.0.0. However, that's not the version used by Github Pages.

The supported version of Jekyll, along with the versions of all its dependencies and extensions are listed on the [Dependency Versions](https://pages.github.com/versions/) page. 

Conveniently, the Github Pages team have released a meta-gem called `github-pages` that depends on exactly the supported versions of the various packages.

### Bundler

The Ruby ecosystem has a tool called `bundler` that handles dependencies and their versions at the project level. 

Install it. From a command prompt, run:

    gem install bundler

### Configuring dependencies

Bundler can now take over installing and running dependencies for our site -- but it needs a configuration file.

In the working directory of your repo, create a file named `Gemfile` with the following content:

	source 'https://rubygems.org'
	gem 'github-pages'
	gem 'wdm', '~> 0.1.0' if Gem.win_platform? 


Now take a deep breath and install everything:

    bundle install

## Preview your site!

Open a command prompt in your repository and:

    bundle exec jekyll serve --watch

If no errors occur, just hit this link: [http://localhost:4000/](http://localhost:4000/)

See that `--watch` at the end? That tells Jekyll to regenerate the site whenever something changes. So the workflow is:

- Make an edit in MarkDown
- Save
- Refresh browser
- Repeat / Repent, as necessary


### Troubleshooting

#### This SSL error:

> SSL_connect returned=1 errno=0 state=SSLv3 read server certificate B: certificate verify failed

You need to download this certificate file: [http://curl.haxx.se/ca/cacert.pem](http://curl.haxx.se/ca/cacert.pem) and add ENV variable `SSL_CERT_FILE` to point to the downloaded file.

More details: 
[https://gist.github.com/fnichol/867550](https://gist.github.com/fnichol/867550) 

Happy blogging!