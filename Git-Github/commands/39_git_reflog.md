# git reflog — Your Safety Net for Lost Commits

## What it does
Records every position HEAD has been in — every checkout,
reset, commit, merge, and rebase. Lets you recover almost
anything you think you destroyed.

## Syntax
```bash
git reflog                           # full reflog
git reflog --oneline                 # compact view
git reset --hard HEAD@{2}            # go back to that position
git reset --hard 9f8e7d6             # by commit hash
```

## My Terminal Output
```bash
rushi@rushi:~/Cloud-Devops$ git reflog
f7a8b9c HEAD@{0}: commit: docs: add git blame notes
a1b2c3d HEAD@{1}: reset: moving to HEAD~1
9f8e7d6 HEAD@{2}: commit: feat: add health check script
c696b11 HEAD@{3}: checkout: moving from feature to main

# I accidentally reset and lost a commit
# I can see it at HEAD@{2}
rushi@rushi:~/Cloud-Devops$ git reset --hard 9f8e7d6
HEAD is now at 9f8e7d6 feat: add health check script
# commit is back
```

## Key Points
- Reflog is LOCAL only — not pushed to GitHub
- Entries expire after 90 days by default
- Before panicking about lost commits, always run `git reflog` first
- Works even after `git reset --hard`, `git rebase`, and deleted branches
- `HEAD@{0}` is current, `HEAD@{1}` is one step back, and so on

## Recovery workflow
```bash
# step 1 — find the lost commit
git reflog

# step 2 — check what it contains
git show 9f8e7d6

# step 3 — recover it
git reset --hard 9f8e7d6
# or create a branch at that point
git branch recovered-work 9f8e7d6
```

## When I use this
Any time I think I lost work — after an accidental reset,
a confused rebase, or deleting the wrong branch.
