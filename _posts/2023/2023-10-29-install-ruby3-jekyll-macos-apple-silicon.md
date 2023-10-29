---
layout: post
cover: false
navigation: true
title: Install Ruby 3 and Jekyll on Apple Silicon
date: 2023-10-29 10:18:00
tags: macos ruby
subclass: 'post'
author: darek
categories: macos ruby
---

If you would like to start your journey with [Jekyll](https://jekyllrb.com/) but need the latest version of Ruby to run your gems, you will need to install Ruby in a slightly tricky way. 
Unfortunately, MacOS, by default, has an old and unsupported version of Ruby (2.6.6). To update it, you will need to take a few steps (a simple installation of Ruby is not sufficient).

### Prerequirements

Before we start we need to install few tools

1. Xcode - Apple IDE
```bash
xcode-select --install
```
2. Homebrew - package manager for MacOS
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
3. [```rbenv```](https://github.com/rbenv/rbenv) is a tool that helps managing multiple Ruby versions, it allows for quick switch between versions. [ruby-build](https://github.com/rbenv/ruby-build) simplifies installation of any Ruby version.
```bash
brew install rbenv ruby-build
```

#### Initialize rbenv

First we need to initialize rbenv

```bash
rbenv init
```

And configure autorun in your shell

a. If you are using **zsh**

```bash
echo 'eval "$(rbenv init - zsh)"' >> ~/.zshrc
```

b. For bash users

```bash
echo 'eval "$(rbenv init - bash)"' >> ~/.bash_profile
```

At this moment you can verify if everything works as expected by running ```rbenv-doctor```

```bash
curl -fsSL https://github.com/rbenv/rbenv-installer/raw/main/bin/rbenv-doctor | bash
```



##### Install Ruby

You can check what versions of Ruby are available by running

```bash
rbenv install -l
```

Install selected version of Ruby (3.2.2 is lates one for me)

```bash
rbenv install 3.2.2
```

When instalation is completed you can set version that will be used globally

```bash
rbenv global 3.2.2
```

To verify installation check **Ruby** version

```bash
ruby -v
```



#### Install Jekyll

Now when we have installed Ruby we can proceed with Jekyll installation.

Best option to install Jekyll is to do user-install and install jekyll in user directory.

```bash
gem install --user-install bundler jekyll
```

When installation finish you can try to use it on jekyll projects (try some from jekyll themes).

To start jekyll run command 

```bash
bundle exec jekyll serve
```

At first You can get errors related to required gems not found, to fix that just install missing gems using command

```bash
gem install GEM_NAME
```

or use bundler

```bash
bundle init
```

Done!