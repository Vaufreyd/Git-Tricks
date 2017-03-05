# Git-Tricks
You will find here some tricks about git usage. Hope it could help you.

## Update git submodule to head revision

Idea here is to change a submodule to head revision. This script take a submodule folder as
parameter.

```
#!/bin/sh
if [ "$#" -ne 1 ] || ! [ -d "$1" ]; then
  echo "Usage: $0 Submodule" >&2
  exit 1
fi

cd $1
git checkout master
git pull origin master
cd ..
git add $1
git commit -m "Update $1 submodule to head"
echo done
```