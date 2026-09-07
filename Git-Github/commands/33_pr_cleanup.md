# After a PR is Merged — Cleanup Workflow

## What it does
Syncs your local machine with the merged changes and removes
the finished branch locally and on GitHub.

## Syntax
```bash
# go back to main and get the merged code
git switch main
git pull

# delete local branch
git branch -d feature-login

# delete remote branch
git push origin --delete feature-login
```

## My Terminal Output
```bash
rushi@rushi:~/Cloud-Devops$ git switch main
Switched to branch 'main'

rushi@rushi:~/Cloud-Devops$ git pull
Updating c696b11..f7a8b9c
Fast-forward
 README.md | 3 +++

rushi@rushi:~/Cloud-Devops$ git branch -d feature-about
Deleted branch feature-about (was a1b2c3d).

rushi@rushi:~/Cloud-Devops$ git push origin --delete feature-about
To git@github.com:DevRushi-engg/Cloud-Devops.git
 - [deleted] feature-about
```

## Key Points
- Always pull main after a merge — your next branch must start
  from the latest code, not stale code
- `-d` only deletes if the branch is fully merged — safe
- `-D` force deletes regardless — use when you abandon a branch
- GitHub also shows a "Delete branch" button on the merged PR page
- Keep your branch list clean — old merged branches add confusion

## Complete post-PR checklist
```bash
git switch main          # 1. go to main
git pull                 # 2. get the merged code
git branch -d name       # 3. delete local branch
git push origin --delete name  # 4. delete remote branch
git log --oneline        # 5. confirm the merge is in history
```

## When I use this
After every merged Pull Request — keeps the repo clean and
ensures the next branch starts from the correct base.
