---
title: "commit"
date: 2017-02-23 16:45:04 +0100
categories: git cmd commit
tags: basic
man: https://www.kernel.org/pub/software/scm/git/docs/git-commit.html
---

> Tells Git to save current validated changes into a commit
> 
	$ git commit -m "<message>"

<div></div> 

> The commit will contains all changes in your working directory, even if you didn't validate them with `git add`
> 
	$ git commit -a -m "<message>"
