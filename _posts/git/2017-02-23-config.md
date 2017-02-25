---
layout: git-post
date: 2017-02-23 16:12:51 +0100
title: "Have a nice Git configuration"
categories: git howto config
tags: config
level: basic
permalink: /git/basic/config
---

Here is a list of usefull commands to have a nice Git configuration. I'll explain them after:

    $ git config --global user.name <your_name>
    $ git config --global user.email <your@mail.com>
    $ git config --global color.ui auto
    $ git config --global status.showUntrackedFiles all
    $ git config --global core.whitespace -trailing-space
    $ git config --global diff.mnemonicPrefix true
    $ git config --global push.default upstream
    $ git config --global log.abbrevCommit true
    $ git config --global alias.hist 'log --pretty=format:\"%h - %d %s (%cr) <%an>\" --graph --date=relative --all'

Now, some explainations:

- `user.name` and `user.mail`: you **MUST** set them. It will identify your commits.
- `color.ui`: Git will use colors (as often as possible) in its messages. They will be more readable.
- `status.showUntrackedFiles`: basically, `git status` will show untracked directories but won't show files in it. With this option, it will only show untracked files.
- `core.whitespace`: this option will force Git to ignore whitespaces related differences when using commands like `git diff`.
- `diff.mnemonicPrefix`: now, `git diff` will tell you between what the diff is done. Instead of `a` and `b`, it will say `c` for Commit, `i` for Index (staging area) and `w` for Working directory.
- `push.default`: by default, Git try to push all branches during a `git push`. So, if you have a very late unused branch locally, the `push` will fail. With this option, Git will only push the active branch.
- `log.abbrevCommit`: limits hash display at 7 characters in `git log`, `git diff`, etc...
- `alias.hist`: create an alias for a pretty nice log with graph and usefull informations. To show it, use `git hist`.

> *Remember*  
> There is hundreds of configuration variables, I just speak about some usefull here. For more informations, see `git help config` or the `CONFIGURATION` section of `git help <cmd>` where &lt;cmd&gt; is the command you want to configure

As a gift, two better aliases for `log`:

    $ git config --global alias.hist 'log --graph --date=relative --all --pretty=format:\"%C(cyan)%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset\"'
    $ git config --global alias.lg 'log --max-count=30 --graph --date=relative --all --pretty=format:\"%C(cyan)%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset\"'

`hist` will show exact the same than the previous, but colored and `lg` too, but only the 30 last posts.