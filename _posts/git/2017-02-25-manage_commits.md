---
layout: git-post
date: 2017-02-25 16:44:50 +0100
title: "Manage commits"
categories: git howto repository
tags: commit reset rebase
level: advanced
permalink: /git/advanced/manage-commits
---

Until the history is published, you can modify commits. But you **must never** modify a published commit.

### Modify the last commit

You forgot a file or a change in your last commit? It's message has a error? Don't panic, you can change that.  
First, prepare a commit as always. Then, just add `--amend` to the commit command:

{% include terminal.html cmds="commit_4" %}

Now if you look the log, you will see that your old last commit is replaced by the new one. The new last commit contains all the old changes plus the new ones, and the new message.

  
You want to totally modify your last commit? Remove a file from it? You can do it too!  
First, go back just before the last commit:

{% include terminal.html cmds="reset_5" %}

Now, prepare your new commit. Then, apply it:

{% include terminal.html cmds="commit_1" %}

This way, you will keep the changes in file and you can remove file(s) content from a commit.

### Modify an older commit / multiples commits

Usefull to clean up the history, you also can use this method to add a change to a previous commit.  
First, find the hash of the commit to edit with `git log` or its alias `git hist` I proposed to you.

Then, go back in history before this commit with `rebase` (to keep changes through the nexts commits):

{% include terminal.html cmds="rebase_3" %}

A prompt will be opened to able you to chose when `rebase` must stop to edit commits. It would look like this:

{% include terminal.html cmds="rebase_1" %}

On the top, replace `pick` by the command (probably `edit`) needed to modify the commit on the lines you want to change something in the commit.  
Once you selected your commits, hit `Ctrl + X`, `y` and `Return` to start the rebase.

If you put an `edit`, the term would show you:
    Stopped at <hash>... <message>
    You can amend the commit now, with

	git commit --amend

    Once you are satisfied with your changes, run

	git rebase --continue
    
    $

Now you can apply the modifications you learned in the first section of this post. When you create your new commit, continue the rebase with

{% include terminal.html cmds="rebase_4" %}

The last `--continue` will display

{% include terminal.html cmds="rebase_5|empty" %}

If something were wrong, you can cancel the process with:

{% include terminal.html cmds="rebase_6" %}
  
To learn more about `rebase` interactive mode, see the [Git Book](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History).
