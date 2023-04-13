
# basic




# split string


```bash
echo "awww|dff|ff|g22" | awk '{split($1,a,"|");print a[4]}'
```