---
layout: post
title: Rename git branch locally and remotely
keywords: git, branch, rename
---

There are three steps to rename git branch locally and remotely.

    git branch -m old_branch new_branch         # Rename branch locally    
    git push origin :old_branch                 # Delete the old branch remotely   
    git push --set-upstream origin new_branch   # Push the new branch, set local branch to track the new remote


And this is also works to rename the currently checked out branch.

    git branch -m new_branch


If you want to delete branch locally and remotely.

    git branch -d old_branch      # delete old_branch locally
    git push origin :old_branch   # delete old_branch remotely
