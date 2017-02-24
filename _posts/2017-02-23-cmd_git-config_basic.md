---
title: "config"
date: 2017-02-23 16:14:09 +0100
categories: git cmd config
tags: basic
man: https://www.kernel.org/pub/software/scm/git/docs/git-config.html
---

> Add / modify a value to all users configuration
> 
    $ git config --system <var> <value>

<div></div> 

> Add / modify a value to user configuration
> 
    $ git config --global <var> <value>

<div></div> 

> Add / modify a value to repository configuration
> 
    $ git config --local <var> <value>

<div></div>

> List all set variables
> 
    $ git config <cfg> -l

<div></div>

> Remove a variable
>
    $ git config <cfg> --unset <var>
