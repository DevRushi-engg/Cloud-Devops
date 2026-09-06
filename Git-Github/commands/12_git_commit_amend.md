# git commit --amend — Fix the Last Commit

## What it does
Rewrites your most recent commit — change the message,
add a forgotten file, or both.

## Syntax
```bash
# fix the commit message only
git commit --amend -m "Better commit message"

# add a forgotten file to the last commit
git add forgotten.txt
git commit --amend --no-edit       # keep same message

# add file AND fix message
git add forgotten.txt
git commit --amend -m "Add notes and forgotten file"
```

## My Terminal Output
```bash
rushi@rushi:~/myproject$ git log --oneline
a1b2c3d Add READM           # typo in message

rushi@rushi:~/myproject$ git commit --amend -m "Add README"
[main b2c3d4e] Add README
 Date: Mon Aug 11 10:00:00 2026

rushi@rushi:~/myproject$ git log --oneline
b2c3d4e Add README          # fixed
```

## Key Points
- Only amend commits that have NOT been pushed yet
- Once pushed to a shared branch, amending rewrites history and causes
  problems for everyone else who has cloned the repo
- `--no-edit` keeps the existing message — just adds the staged files
- The commit gets a new hash — the old one no longer exists

## ⚠️ Rule
```
Never amend a commit you have already pushed to a shared branch.
```

## When I use this
Immediately after committing when I notice a typo in the message
or realize I forgot to include a file.
