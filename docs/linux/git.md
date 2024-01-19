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