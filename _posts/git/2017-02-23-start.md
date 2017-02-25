---
layout: git-post
date: 2017-02-23 16:18:22 +0100
title: "Start a (local) repository"
categories: git howto repository
tags: init clone
level: basic
permalink: /git/basic/start
---

Your Git is well configured, it's time to work! There is two big ways to start a repository:

- It's a new project or an untracked project

Go to your project directory and just run:

    $ git init

That's it! A new repository has been created. If your project already have sources, you will have to add them.

- The project already has a remote repository

Go to your project directory and run:

    $ git init
    $ git clone <path/to/remote.git>

Logically, `<path/to/remote.git>` is given to you by the project maintainer.
With `clone`, you will download all current sources, so you can start ot work!
