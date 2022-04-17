---
title: "Rename Git Branch Locally and Remotely"
date: 2017-03-01
draft: false
authors: ["jiasir"]
categories: ["2017"]
series: ["Git"]
tags: ["Git"]
description: "There are three steps to rename git branch locally and remotely."
---

There are three steps to rename git branch locally and remotely.
```shell
git branch -m old_branch new_branch         # Rename branch locally    
git push origin :old_branch                 # Delete the old branch remotely   
git push --set-upstream origin new_branch   # Push the new branch, set local branch to track the new remote
```

And this is also works to rename the currently checked out branch.
```shell
git branch -m new_branch
```

If you want to delete branch locally and remotely.
```shell
git branch -d old_branch      # delete old_branch locally
git push origin :old_branch   # delete old_branch remotely
```