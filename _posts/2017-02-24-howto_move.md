---
layout: git-post
date: 2017-02-24 19:18:06 +0100
title: "Move or rename file"
categories: git howto repository
tags: rm add mv status
level: basic
permalink: /git/basic/move-rename
---

The file is badly named? It's at the wrong place? Both? No problem, we'll fix that!

    $ mkdir my_dir
    $ mv bad_name.file my_dir/good_name.file
    $ git add my_dir/good_name.file
    $ git rm bad_name.file
    $ git commit -m "rename 'bad_name' to 'good_name' then move it to 'my_dir'"

It's a lot of commands! Do you want a faster way? Allright:

    $ git mv bad_name.file my_dir/good_name.file
    $ git commit -m "rename 'bad_name' to 'good_name' then move it to 'my_dir'"

It's better, isn't it?
