---
layout: default
title: git
parent: LINUX
nav_order: 2
last_modified_date: 2021-03-03
---

## rename users

```shell
git filter-branch --env-filter ' 
OLD_EMAIL="old@email.com" 
NEW_EMAIL="new@email.com" 
NEW_NAME="John Doe" 
if test "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" 
then 
	GIT_AUTHOR_EMAIL=$NEW_EMAIL 
	GIT_AUTHOR_NAME=$NEW_NAME
fi 

if test "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" 
then 
	GIT_COMMITTER_EMAIL=$NEW_EMAIL 
	GIT_COMMITTER_NAME=$NEW_NAME 
fi' -- --all

```


## git subtree 


### add a subtree

```
git subtree add --prefix my-subdirectory http://mysite.com/my_other_project.git master --squash
```


### update a  subtree 

```
git subtree pull --prefix my-subdirectory http://mysite.com/my_other_project.git master --squash

```