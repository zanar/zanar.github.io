---
layout: git-post
date: 2017-02-23 16:33:44 +0100
title: "Add untracked files - Save changes"
categories: git howto repository sources
tags: add commit status
level: basic
permalink: /git/basic/add_commit
---

Your project and your repository are created. Now it's time to say to Git which files must be tracked and save changes.

First of all, a usefull command to know your local repository state:

{% include terminal.html cmds="status_1" %}

Git will show you untracked files, modified files and/or changes to be committed. Worst case?

{% include terminal.html cmds="status_2" %}

The `Untracked files` section shows you all files found in your local repository which doesn't exist in remote repository.  
The `Changed but not updated` section shows you all locally modified files which won't be commited.  
The `Changes to be commited` section shows you modified files which will be commited.

You surely noticed that `<file_1>` is found in `Changed but not updated` **and** `Changes to be commited`. Yes, it is possible. Remember that Git tracks **changes in files**, not files. This status appears when you register a first modification then you modify again the same file.

Now, our goal is to see:

{% include terminal.html cmds="status_3" %}

and here is the walkthrough:

Say to git `I want you to track changes in these files`:

{% include terminal.html cmds="add_1|status_4" %}

Say to Git `I want you to register changes in these files`:

{% include terminal.html cmds="add_2|status_5" %}

Then, `I want you to save all recorded changes`:

{% include terminal.html cmds="commit_1|status_3" %}

Now, all your changes are saved in a commit, but anyone except you knows about that.
> This is the main difference between Git and CVS/SVN: committing something doesn't share changes.
