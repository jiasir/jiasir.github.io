---
title: "Replace Strings With Sed in Directory and Sub Directories"
date: 2017-03-20
draft: false
authors: ["jiasir"]
categories: ["2017"]
series: ["Shell"]
tags: ["Shell"]
description: "Using sed and awk to replace string quickly."
---

The first line occurrences of "foo" will be replaced with "bar". And you can using the second line to check.

```shell
grep -rl 'foo' . | xargs sed -i 's/foo/bar/g'
grep 'foo' -r * | awk -F: {'print $1'} | sort -n | uniq -c
```
