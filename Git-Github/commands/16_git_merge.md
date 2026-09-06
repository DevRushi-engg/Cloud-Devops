# git merge — Combine Branch Work Into Main

## What it does
Brings the commits from one branch into another.
Always switch to the TARGET branch first, then merge.

## Syntax
```bash
# standard merge workflow
git switch main                       # 1. go to target branch
git merge feature-login               # 2. merge the feature in
git branch -d feature-login           # 3. clean up

# cancel a merge that has conflicts
git merge --abort
```

## My Terminal Output
```bash
rushi@rushi:~/myproject$ git switch main
rushi@rushi:~/myproject$ git merge feature-greeting
Updating b2c3d4e..e5f6a7b
Fast-forward
 greet.sh | 1 +
 1 file changed, 1 insertion(+)
 create mode 100755 greet.sh

rushi@rushi:~/myproject$ git branch -d feature-greeting
Deleted branch feature-greeting (was e5f6a7b).
```

## Merge Conflicts
When both branches edited the same lines:
```
<<<<<<< HEAD
your version of the line
=======
their version of the line
>>>>>>> feature-login
```

## Resolving a conflict
```bash
# 1. open the file and edit — delete the marker lines
#    keep what you want, remove <<<<<<< ======= >>>>>>>
nano app.py

# 2. mark resolved
git add app.py

# 3. complete the merge
git commit

# escape hatch — cancel the whole merge
git merge --abort
```

## Key Points
- Always be on the TARGET branch before running `git merge`
- Conflicts are normal — not a disaster — Git is asking you to choose
- `--abort` backs out completely and returns to the state before merge
- `-d` after merging cleans up the finished branch
- `git log --oneline --graph` after merging shows the history visually

## When I use this
After finishing a feature branch — merge it back into main,
then delete the branch to keep the repo clean.
