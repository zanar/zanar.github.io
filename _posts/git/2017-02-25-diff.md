---
layout: git-post
date: 2017-02-25 12:29:04 +0100
title: "Check differences"
categories: git howto repository
tags: diff
level: basic
permalink: /git/basic/diff
---

`diff` is a powerfull and usefull tool. It can show you changes in files, between commits or branches, and many other!

Let's start with the beginning:

    $ git diff

This simple command will show you differences between working directory and index.  
By adding the `--cached` option, the output will be the differences between index and last commit.  
And the `HEAD` option extract differences between the last commit and the working directory.

Then, if you specify a file or a directory:

    $ git diff <path>

The output will be limited to the file or the directory and will be made between the same origins than previously. You can also add `--cached` or `HEAD` option.

You can specify two commits to compare:

    $ git diff <hash_1>..<hash_2>

to show differences bewteen them. The **..** between <hash_1> and <hash_2> is very important.

Finnally, a last option: `--stat`. The output will be:

    $ git diff --stat
    <file_1> | 2 +-
    <file_2> | 10 ++++------
    <file_3> | 4 +++-
    3 files changed, 8 insertions(+), 7 deletions(-)

This option doesn't work for `git diff <file>`.