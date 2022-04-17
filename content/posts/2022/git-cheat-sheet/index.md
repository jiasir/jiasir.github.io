+++ 
draft = false
date = 2022-04-17T17:38:22+08:00
title = "Git Cheat Sheet"
description = ""
slug = ""
authors = ["jiasir"]
tags = ["Git"]
categories = ["2022"]
externalLink = ""
series = ["Git"]
+++

# Commits的关联关系
* Git用username关联commits
* GitHub用电子邮件关联commits

# 全局设置
```shell
git config --global user.name "user-name" # 设置username
git config --global user.email "email" # 设置email
git config --global credential.helper osxkeychain # 设置密码通过osxkeychain保存
```

# 仓库级别设置
```shell
git config user.name "user-name"
git config user.email "email"
```

# 列出全局设置
```shell
git config --global --list
```

# 设置upstream
```shell
git branch -u origin/branch_name # 设定当前分支的upstream为origin/branch_name

```

# 删除remote branch
```shell
git branch -d branch_name # delete local branch
git push origin :branch_name # delete remote branch
git push -d origin branch_name # delete remote branch
```

# Find branch tracking
```shell
git remote show origin
```

# Push local new branch to remote
```shell
git branch branch_name
git checkout branch_name
git push -u origin branch_name
# 注意格式： git push [remote] [local_branch] [remote_branch]，如果remote_branch没有local_branch，则会被创建
```

# 设置credential helper
```shell
git config --global credential.helper osxkeychain
git credential-osxkeychain store # 存储
git credential-osxkeychain get # 获取
git credential-osxkeychain erase # 删除
```

# Merge远程分支
```shell
git fetch origin remote_branch_name
git checkout local_branch_name
git merge origin remote_branch_name # 或者 git merge origin/remote_branch_name
```

# 保持与远程分支一致
```shell
git checkout main
git fetch origin main
git reset --hard origin/main
```

# GitFlow Workflow
```shell
git checkout main
git checkout -b develop
git checkout -b feature_branch
# work happens on feature branch
git checkout develop
git merge feature_branch
git checkout main
git merge develop
git branch -d feature_branch
```

# GitFlow Workflow with hotfix
```shell
git checkout main
git checkout -b hotfix_branch
# work is done commits are added to the hotfix_branch
git checkout develop
git merge hotfix_branch
git checkout main
git merge hotfix_branch
```

# 更改最近的commit message
```shell
git commit --amend # on local branch
git --force-with-lease origin remote_branch # on remote branch
```

# Merge a pull request
```shell
git fetch origin pull/pr_id/head:new_local_branch # fetch pr id 并且创建新本地分支
git checkout new_local_branch # 切换到这个被创建的分支做一些测试
git fetch origin pull/pr_id/head && git merge origin/pull/pr_id/head # 如果pr更新了，则拉到本地
git checkout master && git merge new_local_branch
```

# Merge with a merge commit
```shell
git merge --no-ff branch_name
```

# Update submodule
```shell
git submodule update --recursive --remote

```
