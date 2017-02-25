---
layout: git-post
date: 2017-02-24 18:45:59 +0100
title: "Cancel changes"
categories: git howto repository
tags: status checkout reset
level: basic
permalink: /git/basic/cancel-modif
---

In this post, you will learn how to cancel files modifications, before or after staging them.

### After staging

Current repository state:

    $ git status
    # On branch <branch>
    # Changes to be committed:
    #   (use "git reset HEAD <file>..." to unstage)
    #
    #	modified:   <file_1>
    #	modified:   <file_2>
    # 	modified:   <file_3>

Did you noticed? `status` output tell us how to do and we'll follow the tip:

    $ git reset HEAD <file_1>
    $ git status
    # On branch <branch>
    # Changes to be committed:
    #   (use "git reset HEAD <file>..." to unstage)
    #
    #	modified:   <file_2>
    # 	modified:   <file_3>
    #
    # Changes not staged for commit:
    #   (use "git add <file>..." to update what will be committed)
    #   (use "git checkout -- <file>..." to discard changes in working directory)
    #
    #	modified:   <file_1>

we also can do:

    $ git reset HEAD <file_1> <file_2>
    $ git status
    # On branch <branch>
    # Changes to be committed:
    #   (use "git reset HEAD <file>..." to unstage)
    #
    # 	modified:   <file_3>
    #
    # Changes not staged for commit:
    #   (use "git add <file>..." to update what will be committed)
    #   (use "git checkout -- <file>..." to discard changes in working directory)
    #
    #	modified:   <file_1>
    #	modified:   <file_2>

or, obviously:

    $ git reset HEAD
    $ git status
    # Changes not staged for commit:
    #   (use "git add <file>..." to update what will be committed)
    #   (use "git checkout -- <file>..." to discard changes in working directory)
    #
    #	modified:   <file_1>
    #	modified:   <file_2>
    # 	modified:   <file_3>

### Before staging

or after removed from index  
  
This time, the repository state is:

    $ git status
    # On branch <branch>
    # Changes not staged for commit:
    #   (use "git add <file>..." to update what will be committed)
    #   (use "git checkout -- <file>..." to discard changes in working directory)
    #
    #	modified:   <file_1>
    #	modified:   <file_2>
    # 	modified:   <file_3>
    #
    no changes added to commit (use "git add" and/or "git commit -a")

Again, let's use the tip:

    $ git checkout <file_1>
    $ git status
    # On branch <branch>
    # Changes not staged for commit:
    #   (use "git add <file>..." to update what will be committed)
    #   (use "git checkout -- <file>..." to discard changes in working directory)
    #
    #	modified:   <file_2>
    # 	modified:   <file_3>
    #
    no changes added to commit (use "git add" and/or "git commit -a")

for multiple files:

    $ git checkout <file_1> <file_2>
    $ git status
    # On branch <branch>
    # Changes not staged for commit:
    #   (use "git add <file>..." to update what will be committed)
    #   (use "git checkout -- <file>..." to discard changes in working directory)
    #
    # 	modified:   <file_3>
    #
    no changes added to commit (use "git add" and/or "git commit -a")

or for all files:

    $ git checkout <branch>
    $ git status
    # On branch <branch>
    nothing to commit (working directory clean)

It's wierd but also obvious to use `checkout`: somewhere, undo changes is a "navigation" to the last commit.
