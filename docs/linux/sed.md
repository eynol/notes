---
layout: default
title: sed
parent: SHELL
nav_order: 3
---


### basic


```bash
echo 'abcdefj'| sed 's/abc/dd/'

```


```bash
sed -E "s/^(\s+)([^\"]\S+[^'\"])(\s+):(\s+)'(\S+)'/\1\"\2\"\3:\4\"\5\"/" tsed.txt
```


#### -i option
replace Inplace

```bash
echo "nich to meet you" >> test.txt
sed -i test.txt 's/meet/see/'
cat test.txt

```
