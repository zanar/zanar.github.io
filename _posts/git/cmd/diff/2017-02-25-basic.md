---
title: "diff"
date: 2017-02-25 11:53:03 +0100
categories: git cmd diff
tags: basic
man: https://www.kernel.org/pub/software/scm/git/docs/git-diff.html
---

> Compare file
> 
    $ git diff <file>            # between working dir and index
    $ git diff --cached <file>   # between index and last commit
    $ git diff HEAD <file>       # between working dir and las commit

<div></div> 

> Compare commits
>
    $ git diff <hash_1>..<hash_2>

<div></div>

> Compare directories
>
    $ git diff            # working dir v. index
    $ git diff --cached   # index v. last commit
    $ git diff HEAD       # working dir v. last index

<div></div>

> Show only changes statistics
>
    $ git diff --stat