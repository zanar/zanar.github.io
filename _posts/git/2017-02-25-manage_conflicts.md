---
layout: git-post
date: 2017-02-25 18:54:58 +0100
title: "Manage conflicts"
categories: git howto repository
tags: merge 
level: advanced
permalink: /git/advanced/manage-conflicts
---

Sometimes, merging fails.

    $ git merge <branch>
    Auto-merging <file>
    CONFLICT (content): Merge conflict in <file>
    Automatic merge failed; fix conflicts and then commit the result.

The main reason is that changes happened in <branch> and 'master' in <file> at the same location. Then, `merge` breaks before creating the merge commit as `status` can tell you:

    $ git status
    On branch master
    You have unmerged paths.
    (fix conflicts and run "git commit")

    Unmerged paths:
    (use "git add <file>..." to mark resolution)

	both modified:      <file>

    no changes added to commit (use "git add" and/or "git commit -a")

Open unmerged files, you will find something like this:

    <<<<<<< HEAD:<file>
    modif_1
    =======
    modif_2
    >>>>>>> <branch>:<file>

Replace the bloc with the right change, and close your editor (this action is named "conflict resolution"). After resolving each conflicts in each files, run `git add` on each files then `git commit`. This will show you:

    Merge branch '<branch>'

    Conflicts:
	<file>
    #
    # It looks like you may be committing a merge.
    # If this is not correct, please remove the file
    #	.git/MERGE_HEAD
    # and try again.


    # Please enter the commit message for your changes. Lines starting
    # with '#' will be ignored, and an empty message aborts the commit.
    # On branch master
    # All conflicts fixed but you are still merging.
    #
    # Changes to be committed:
    #	modified:   <file>
    #

You can modify the message if you want, then exit. The `merge` ended!
