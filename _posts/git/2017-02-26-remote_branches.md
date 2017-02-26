---
layout: git-post
date: 2017-02-26 13:57:03 +0100
title: "Work with (remote) branches"
categories: git howto repository
tags: push pull checkout
level: advanced
permalink: /git/advanced/remote-branches
---

This post will explain how to work with remote branches.

### Create a remote branch

The basic command to create a local branch remotely tracked is

    $ git checkout -b <local_branch> <remote>/<remote_branch>
    Branch <local_branch> set up to track remote branch <remote_branch> from <remote>.
    Switched to a new branch '<local_branch>'

With this command, you can set different names for local and remote branch. Or, if you want to use the same name, you can run the shortcut command:

    $ git checkout --track <remote>/<branch>
    Branch <branch> set up to track remote branch <branch> from <remote>.
    Switched to a new branch '<branch>'

### Make a local branch tracked

You already have a local branch and you want to track it remotely? It is possible:

    $ git push <remote> <branch>

### Follow and share in remote branches

To download datas from / upload datas to a remote branch, you can use the same commands than for 'master', with specifying the branch name:

    $ git push <remote> <branch>
    $ git pull --rebase=prevent <branch>

For the `pull` command, you can avoid the `--rebase` option if you set the `pull.rebase` config at `prevent`.

### Delete a remote branch

**Be really carefull with this command.** Before using it, say your collaborators that this branch is done and be sure it won't be used again.

    $ git push origin --delete <branch>
