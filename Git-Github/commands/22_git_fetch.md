# git fetch — Download Without Merging

## What it does
Downloads new commits and branches from the remote but does NOT
apply them to your working branch. Lets you look before you leap.

## Syntax
```bash
git fetch                       # fetch from origin
git fetch origin                # same, explicit
git fetch origin main           # fetch one branch only
git log origin/main --oneline   # see what was fetched
```

## My Terminal Output
```bash
rushi@rushi:~/Cloud-Devops$ git fetch origin
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
From git@github.com:DevRushi-engg/Cloud-Devops
   c696b11..d4e5f6a  main -> origin/main

# see what changed without merging it
rushi@rushi:~/Cloud-Devops$ git log origin/main --oneline
d4e5f6a docs: add new command file
c696b11 fix: resolve README conflict

# now decide to merge
rushi@rushi:~/Cloud-Devops$ git merge origin/main
```

## Key Points
- Safe to run at any time — never changes your working files
- After fetching, use `git log origin/main` to inspect before merging
- `git pull` = `git fetch` + `git merge` — pull is the shortcut
- Useful when you want to check what teammates committed before merging
- Remote tracking branches like `origin/main` are updated by fetch

## When I use this
When I want to check what changed on the remote before
merging it into my branch — look before you leap.
