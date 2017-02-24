---
layout: git-post
date: 2017-02-23 16:50:25 +0100
title: "Show commit logs"
categories: git howto repository
tags: log
level: basic
permalink: /git/basic/log
---

There is a lot of reasons to want to / have to show what append in commit logs. So remember, commit logs is at least as important as source codes.

There is a git command to show commit logs. Without any options, it will show you all parents commit of your current version: `git log`

    $ git log
    commit 7950659dc9ef7f2b50b18010622299c508bfdfc3
	Author: author <author (at) mail.com>
	Date:   Fri Feb 21 00:00:32 2014 +0100
	
	    commit message
	
	commit 221243eb14415fdda82f250b687203a9b86e7f08
	Author: author <author (at) mail.com>
	Date:   Fri Feb 20 15:52:14 2014 +0100
	
	    other message
	
	commit f491239170cb1463c7c3cd970862d6de636ba787
	Author: author <author (at) mail.com>
	Date:   Fri Feb 18 12:00:01 2014 +0100
	
	    message

If you activated `log.abbrevCommit` in your configuration, the output will be:

    $ git log
    commit 7950659
	Author: author <author (at) mail.com>
	Date:   Fri Feb 21 00:00:32 2014 +0100
	
	    commit message
	
	commit 221243e
	Author: author <author (at) mail.com>
	Date:   Fri Feb 20 15:52:14 2014 +0100
	
	    other message
	
	commit f491239
	Author: author <author (at) mail.com>
	Date:   Fri Feb 18 12:00:01 2014 +0100
	
	    message

There is a lot of options with `log` (more than a hundred!), to filter them before display or show more informations about each commits.
If you defined the `hist` alias like me, you will be able to see:

    $ git hist
    * 7950659 - (HEAD, master) commit message <author> (10 minutes ago)
    | * 41ab9d8 - (my_branch) branch commit message <author2> (15minutes ago)
    |/
    * 221243e - other message <author> (1 day ago)
    * f491239 - message <author> (3 day ago)
