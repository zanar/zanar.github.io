---
title: "branch"
date: 2017-02-24 21:22:24 +0100
categories: git cmd branch
tags: advanced
man: https://www.kernel.org/pub/software/scm/git/docs/git-branch.html
---

> Create a branch
> 
    $ git branch <name>

<div></div>

> List branches
>
    $ git branch        # local branches
    $ git branch -r     # remotes branches
    $ git branch --all  # all tracked branches

<div></div>

> Delete a **merged** branch
>
    $ git branch -d <name>

<div></div>

> Delete a **useless** branch
>
    $ git branch -D <name>
