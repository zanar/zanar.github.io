---
title: "merge"
date: 2017-02-24 21:46:53 +0100
categories: git cmd merge
tags: advanced
man: https://www.kernel.org/pub/software/scm/git/docs/git-merge.html
---

> Merge &lt;branch&gt; in current branch
> 
    $ git merge <branch>

<div></div>

> Merge &lt;branch&gt; in current branch with ensure that it will remain in logs
>
    $ git merge --no-ff <branch>

<div></div>

> Merge &lt;branch&gt; in current branch with ensure that it will remain in logs with a message for the merge commit
>
    $ git merge --no-ff <branch> -m "message"
