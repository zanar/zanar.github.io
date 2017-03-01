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

{% include terminal.html cmds="checkout_8" %}

With this command, you can set different names for local and remote branch. Or, if you want to use the same name, you can run the shortcut command:

{% include terminal.html cmds="checkout_9" %}

### Make a local branch tracked

You already have a local branch and you want to track it remotely? It is possible:

{% include terminal.html cmds="push_4" %}

### Follow and share in remote branches

To download datas from / upload datas to a remote branch, you can use the same commands than for 'master', with specifying the branch name:

{% include terminal.html cmds="push_4|pull_2" %}

For the `pull` command, you can avoid the `--rebase` option if you set the `pull.rebase` config at `prevent` with the `--no-rebase` option.

### Delete a remote branch

**Be really carefull with this command.** Before using it, say your collaborators that this branch is done and be sure it won't be used again.

{% include terminal.html cmds="push_5" %}
