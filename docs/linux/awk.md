---
layout: default
title: awk
parent: SHELL
nav_order: 1
last_modified_date: 2024-01-20
---

# AWK




## split string


```bash
echo "awww|dff|ff|g22" | awk '{split($1,a,"|");print a[4]}'
```