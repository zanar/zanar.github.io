---
layout: git-post
date: 2017-02-25 11:12:19 +0100
title: "Manage changes"
categories: git howto repository
tags: add reset
level: advanced
permalink: /git/advanced/manage-modif
---

This post explain how to add / remove some changes from index before a commit.

### Partially add changes

You opened a file for a fix, but you did other (needed) changes unconnected with the reason why you firstly opened the file: an atomic commit is impossible.  
**Do not** put all your changes in a commit with a message like "lots of changes"... use `add -p`!
The `-p` option, aka `--patch`, allows you to chose which hunks of changes you will add to the stage for the commit.

{% include terminal.html cmds="status_12|add_3|status_13|commit_2|empty|add_3|status_16|commit_3|empty|status_3" %}

As you noticed, after a `add -p`, the file is in the `Changes to be commited` section and the `Changed but not updated` section. Obviously. A part of changes is staged, the other part isn't.  

> **Warning:**  
> **Never** use `commit -a` after a `add -p` or you will lose all your "ninja" work with hunks.

With the `-p` option, `git add` will cut changes in hunks and will ask you if you want to add this hunk to stage or not. Hunks are made using unchanged lines, so if two changes are too close they will be put in one hunk. But Git will offer you a lot of functions during the process and you will be able to split or edit hunks.

### Partially remove changes

You staged a file with `git add` but you want to remove a change from the stage? `reset` offers you the solution with the `-p` option!

{% include terminal.html cmds="reset_4" %}

This is exactly the opposite of `git add -p`, you will be able to chose which hunks you want to remove.
