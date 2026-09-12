# Pushing Branches — Sharing Feature Branches on GitHub

## What it does
Publishes a local branch to GitHub so teammates can see it,
review it, and open a pull request.
Branches are local until you explicitly push them.

## Syntax
```bash
git switch -c feature-login          # create branch
# do work and commit
git push -u origin feature-login     # publish to GitHub

# delete remote branch after merge
git push origin --delete feature-login
```

## My Terminal Output
```bash
rushi@rushi:~/Cloud-Devops$ git switch -c feature-login
Switched to a new branch 'feature-login'

rushi@rushi:~/Cloud-Devops$ git add login.md
rushi@rushi:~/Cloud-Devops$ git commit -m "feat: add login notes"
[feature-login a1b2c3d] feat: add login notes

rushi@rushi:~/Cloud-Devops$ git push -u origin feature-login
Enumerating objects: 4, done.
To git@github.com:DevRushi-engg/Cloud-Devops.git
 * [new branch]  feature-login -> feature-login
branch 'feature-login' set up to track 'origin/feature-login'.
```

## Key Points
- `-u origin feature-login` publishes and links the branch in one step
- After this, plain `git push` works for that branch too
- This is the first step of a Pull Request workflow
- Teammates can now check out your branch and review it
- After the PR is merged, delete the remote branch to keep things clean

## When I use this
After finishing work on a feature branch and wanting to open
a Pull Request for review on GitHub.
