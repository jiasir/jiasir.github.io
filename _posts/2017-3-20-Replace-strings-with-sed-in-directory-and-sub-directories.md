---
layout: post
title: Replace strings with sed in directory and sub directories
keywords: sed, replace, sub directories
---

The first line occurrences of "foo" will be replaced with "bar". And you can using the second line to check.

```shell
grep -rl 'foo' . | xargs sed -i 's/foo/bar/g'
grep 'foo' -r * | awk -F: {'print $1'} | sort -n | uniq -c
```
