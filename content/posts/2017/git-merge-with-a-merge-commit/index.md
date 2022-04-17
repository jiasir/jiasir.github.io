---
title: "Git Merge With a Merge Commit"
date: 2017-03-02
draft: false
authors: ["jiasir"]
categories: ["2017"]
series: ["Git"]
tags: ["Git"]
description: "Using `git merge --no-ff` to merge with a merge commit."
---

Git does a fast forward when you merge branch that is ahead of your checked-out branch, git only update the branch pointer. Some people don't like that and want to see a explicit merge.

![Git merge with a merge commit](git-merge-with-a-merge-commit.png)
```shell
git checkout develop
git merge --no-ff myfeature
git push origin develop
```
The `--no-ff` flag causes the merge to always create a new commit object, even if the merge could be performed with a fast-forward. This avoids losing information about the historical existence of a feature branch and groups together all commits that together added the feature.
