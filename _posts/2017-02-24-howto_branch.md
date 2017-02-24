---
layout: git-post
date: 2017-02-24 21:20:35 +0100
title: "Work with (local) branches"
categories: git howto repository
tags: branch checkout merge rebase
level: advanced
permalink: /git/advanced/branch
---

A single Git repository can maintain a lots of development branches. You want to try an idea, make some experimental changes, fix a bug out of master, or just try a different way without sharing it? Create a new branch!

In a branch, you can work exactly as if you were in the 'master': add, commit, rm, mv, etc... but until you explicitly say it, a local branch won't be tracked by remote repositories.

### Create 

How to create a branch and go in it:

    $ git branch <name>
    $ git checkout <name>

or the short way:

    $ git checkout -b <name>

If you want to know tracked branches, just do:

    $ git branch         # to know local branches
    $ git branch -r      # to know remote branches
    $ git branch --all   # to know all branches

### Merge

This is a small introduction about merging branches.  
Your developments in a branch is fine, so you want to add it in the 'main' branch or in a remote branch. It's called a merge and you must be very carefull when you do it.

As example, let's say that your local branch is named "experimental" and the remote branch is "master", and we want to merge "experimental" in "master".
  
First, you must answer this question: "Is experimental a usefull branch?" or with other words, "Do I want to keep this branch in logs?".

If "yes", you just have to do:

    $ git checkout master		# and be sure to have all new commits if any
    $ git merge --no-ff experimental
    # or
    $ got merge --no-ff experimental -m "merge reasons"

The `--no-ff` option ensures that your branch will remain in logs, even if 'master' doesn't have new commits.
  
If "no", and 'master' has not new commits while your devs in 'experimental', just do a simple `merge`:

    $ git checkout master
    $ git merge experimental

If "no" and 'master' has new commits, you will have to `rebase` your branch before merging:

    $ git checkout experimental
    $ git rebase master experimental
    $ git checkout master
    $ git merge experimental

I'll explain it in details in a future post, but just a little word about `rebase`: with this command, you will "move" your branch start, by adding all missing commits from 'master'.

> **So, for those who say that `merge` and `rebase` do the same, it's wrong!!** at least if you want to keep a clean log...

### Delete

Your idea was wrong and/or the branch is not needed anymore: delete it.

    $ git branch -D <name>
