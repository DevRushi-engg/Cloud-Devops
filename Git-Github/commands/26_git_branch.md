# git branch -M — Rename a Branch

## What it does
Renames the current branch.
Most commonly used to rename the default branch
from `master` to `main` before the first push.

## Syntax
```bash
git branch -M main          # rename current branch to main
git branch -m old new       # rename any branch by name
```

## My Terminal Output
```bash
rushi@rushi:~/myproject$ git branch
* master

rushi@rushi:~/myproject$ git branch -M main
rushi@rushi:~/myproject$ git branch
* main
```

## Key Points
- `-M` is force rename — works even if a branch named `main` already exists
- `-m` is a safe rename — will not overwrite an existing branch name
- GitHub now defaults to `main` — always rename before first push
- The full first push sequence for a new project:

```bash
git init
git add .
git commit -m "init: first commit"
git branch -M main
git remote add origin git@github.com:user/repo.git
git push -u origin main
```

## When I use this
Once per new project — right before the first push to GitHub
to ensure the branch is named `main` not `master`.
