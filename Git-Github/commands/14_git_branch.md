# git branch — Create and Manage Branches

## What it does
A branch is a separate line of work split off from main.
Build a feature without touching the working version.
If it fails, delete the branch — nothing is harmed.

## Syntax
```bash
git branch                      # list all branches (* = current)
git branch feature-login        # create a new branch
git branch -d feature-login     # delete a merged branch
git branch -D feature-login     # force delete unmerged branch
```

## My Terminal Output
```bash
rushi@rushi:~/myproject$ git branch
* main

rushi@rushi:~/myproject$ git branch feature-login
rushi@rushi:~/myproject$ git branch
  feature-login
* main

rushi@rushi:~/myproject$ git branch -d feature-login
Deleted branch feature-login (was b2c3d4e).
```

## How branching looks
```
main    ──●──●──●──────────────●──
                  \           /
feature            ●──●──●──●
```
Branch off main → do the work → merge back → delete the branch.
Main stays stable the whole time.

## Key Points
- `*` marks the branch you are currently on
- Branches are cheap and instant in Git — make one for every new task
- `-d` only deletes if the branch has been merged — safe
- `-D` force deletes regardless — be careful
- All branches share the same commit history up to the point they split

## When I use this
Every new feature, bug fix, or experiment gets its own branch.
Never work directly on main for anything beyond tiny fixes.

