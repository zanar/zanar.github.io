---
title: "log"
date: 2017-02-23 16:58:59 +0100
categories: git cmd log
tags: advanced
man: https://www.kernel.org/pub/software/scm/git/docs/git-log.html
---

> Each commit on one line (only hash and message)
> 
    $ git log --pretty=oneline

<div></div> 
    
> The two last commits
> 
    $ git log --max-count=2

<div></div> 

> All commits in the branch younger than 5 minutes
> 
    $ git log --since='5 minutes ago'

<div></div> 

> All commits in the branch older than 1 day
> 
    $ git log --until='1 day ago'

<div></div> 

> All commits from this author
> 
    $ git log --author=<name>

<div></div> 

> All commits from all branches
> 
    $ git log --all

<div></div> 

> All commits with an 'ascii' graph
> 
    $ git log --graph --all

<div></div> 

> Shows the changed files list and number of added/removed lines
> 
    $ git log --stat

<div></div> 

> Shows the commits patches
> 
    $ git log -p
