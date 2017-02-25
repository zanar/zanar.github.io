---
layout: git-post
date: 2017-02-24 21:53:54 +0100
title: "Branches: merge versus rebase"
categories: git howto repository
tags: merge rebase
level: advanced
permalink: /git/advanced/merge-rebase
---

I know, there is a big debate around this question. But if we look at how works these commands, the difference is big and there usages are clear. Let's see it.

Here is the schematic of the repository before merging / rebasing:

            e --- f --- g sandbox
           /
    a --- b --- c--- d master

### Merge

When you apply the `$ git merge sandbox` at the master `HEAD`, the result will be:

            e ---  f  --- g sandbox
           /               \
    a --- b --- c --- d --- h master

The `h` commit will contain changes from `d` and `g`, and the commit history is preserved.  
In the facts, Git will apply `e`, `f` and `g` to `d` and store the result in a new commit `h`.

### Rebase

When you apply the `$ git rebase master` at the sandbox `HEAD`, the result will be:

                        e' -- f' -- g' sandbox
                       /
    a --- b --- c --- d master

At this point, `g'` will contain changes from `g` and `d`, but the commits `e`, `f` and `g` doesn't exist anymore.  
In the facts, Git will apply `c` and `d` to `e` and create `e'`, to `f` and create `f'` then to `g` to create `g'`

### Differences

So yes, `g'` and `h` will be the same if we look the source codes, but there positions in history are tottally different!
As abstract, we can tell:

> `merge` merges branches into a new commit  
> `rebase` change the start point of a branch

### Usages

Let's come back to the previous post.  
  
The repository can have two schematics:
Schematic A:

            e --- f --- g sandbox
           /
    a --- b --- c--- d master

Schematic B:

            e --- f --- g sandbox
           /
    a --- b master

If you want to keep the branch in the logs, `merge` is the command to use. But with schematic B, a simple `merge` will destroy the branch: it's the fast-forward method.  
So, to be sure to keep it in both case, use the option `--no-ff`:

    $ git checkout master
    $ git merge --no-ff sandbox
 
Result A:

            e ---  f  --- g sandbox
           /               \
    a --- b --- c --- d --- h master

Result B:

            e ---  f  --- g sandbox
           /               \
    a --- b --------------- c master

  
If you don't want to keep the branch in the log, you mustn't use `--no-ff`. But with schematic A, a simple `merge` will keep the branch.  
So here are the solutions:

A:

    $ git checkout sandbox
    $ git rebase master sandbox
    
                        e' -- f' -- g' sandbox
                       /
    a --- b --- c --- d master
    
    $ git checkout master
    $ git merge sandbox
    
                        e' -- f' -- g' sandbox
                       X
    a --- b --- c --- d --- e' --- f' --- g' master

B:

    $ git checkout master
    $ git merge sandbox
    
            e ---  f  --- g sandbox
           X
    a --- b --- e --- f --- g master

In both cases, 'sandbox' branches will be abandonned. A `$ git gc` command will delete them.
