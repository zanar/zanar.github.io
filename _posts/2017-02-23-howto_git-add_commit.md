---
layout: git-post
date: 2017-02-23 16:33:44 +0100
title: "Add untracked files - Save changes"
categories: git howto deposit sources
tags: add commit status
level: basic
permalink: /git/basic/add_commit
---

Your project and your deposit are created. Now it's time to say to Git which files must be tracked and save changes.

First of all, a usefull command to know your local deposit state:

    $ git status

Git will show you untracked files, modified files and/or changes to be committed. Worst case?

    $ git status
    # On branch master
    # Changes to be commited:
    #    (use "git reset HEAD <file>..." to unstage)
    #
    #        modified: <file_1>
    #        modified: <file_2>
    #
    # Changed but not updated:
    #    (use "git add <file>..." to update what will be commited)
    #    (use "git checkout -- <file>..." to discard changes in working directory)
    #    (commit or discard the untracked or modified content in submodules)
    #        modified: <file_1>
    #        modified: <file_3>
    #
    # Untracked files:
    #    (use "git add <file>..." to include in what will be commited)
    #
    #        <file_4>
    #        <file_5>

The `Untracked files` section shows you all files found in your local deposit which doesn't exist in remote deposit.
The `Changed but not updated` section shows you all locally modified files which won't be commited
The `Changes to be commited` section shows you modified files which will be commited

You surely noticed that &lt;file_1&gt; is found in `Changed but not updated` **and** `Changes to be commited`. Yes, it is possible. Remember that Git tracks **changes in files**, not files. This status appears when you register a first modification then you modify again the same file.

Now, our goal is to see:

    $ git status
    # On branch master
    nothing to commit (working directory clean)

and here is the walkthrough:

Say to git `I want you to track changes in these files`:

    $ git add <file_4> <file_5>
    $ git status
    # On branch master
    # Changes to be commited:
    #    (use "git reset HEAD <file>..." to unstage)
    #
    #        modified: <file_1>
    #        modified: <file_2>
    #        modified: <file_4>
    #        modified: <file_5>
    #
    # Changed but not updated:
    #    (use "git add <file>..." to update what will be commited)
    #    (use "git checkout -- <file>..." to discard changes in working directory)
    #    (commit or discard the untracked or modified content in submodules)
    #        modified: <file_1>
    #        modified: <file_3>

Say to Git `I want you to register changes in these files`:

    $ git add <file_1> <file_3>
    $ git status
    # On branch master
    # Changes to be commited:
    #    (use "git reset HEAD <file>..." to unstage)
    #
    #        modified: <file_1>
    #        modified: <file_2>
    #        modified: <file_3>
    #        modified: <file_4>
    #        modified: <file_5>

Then, `I want you to save all recorded changes`:

    $ git commit -m "message that explain the commit"
    $ git status
    # On branch master
    nothing to commit (working directory clean)

Now, all your changes are saved in a commit, but anyone except you knows about that.
> This is the main difference between Git and CVS/SVN: committing something doesn't share changes.
