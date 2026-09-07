# git rebase — Replay Commits on Top of Another Branch

## What it does
Moves your commits to sit on top of another branch, creating
a clean straight line of history.
Rewrites commit IDs — so never use on shared branches.

## Syntax
```bash
git switch feature-login
git rebase main              # replay feature commits on top of main
git rebase --abort           # back out safely at any point
git rebase --continue        # after resolving a conflict mid-rebase
```

## My Terminal Output
```bash
rushi@rushi:~/Cloud-Devops$ git switch feature-login
rushi@rushi:~/Cloud-Devops$ git rebase main
Successfully rebased and updated refs/heads/feature-login.

rushi@rushi:~/Cloud-Devops$ git log --oneline
e5f6a7b feat: add login notes    ← replayed on top
d4e5f6a docs: update README      ← main's latest commit
c696b11 fix: resolve conflict
```

## What rebase looks like
```
Before rebase:
main:        A─B─C
feature-login:   ├─D─E

After rebase:
main:        A─B─C
feature-login:       C─D'─E'
```
D and E are replayed as D' and E' — same changes, new commit IDs.

## Rebase conflict workflow
```bash
# conflict stops the rebase
git rebase main
# CONFLICT: fix the file
nano conflicting-file.md
git add conflicting-file.md
git rebase --continue        # move to next commit
# or cancel entirely
git rebase --abort
```

## ⚠️ The Golden Rule
```
Never rebase commits you have already pushed and shared.
```
Rebasing rewrites commit IDs. If teammates pulled your old commits,
their repos will conflict with your rewritten ones.

## When I use this
Cleaning up my own local feature branch before opening a PR —
to present a tidy linear history. Never after pushing.
