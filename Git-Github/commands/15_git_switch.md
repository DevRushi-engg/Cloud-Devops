# git switch — Move Between Branches

## What it does
Switches your working directory to a different branch.
The modern replacement for `git checkout` for branch operations.

## Syntax
```bash
git switch main                  # switch to main
git switch feature-login         # switch to existing branch
git switch -c feature-login      # create AND switch in one step
git switch -c hotfix main        # create from main specifically
```

## My Terminal Output
```bash
rushi@rushi:~/myproject$ git switch -c feature-greeting
Switched to a new branch 'feature-greeting'

rushi@rushi:~/myproject$ git branch
* feature-greeting
  main

rushi@rushi:~/myproject$ git switch main
Switched to branch 'main'
```

## Key Points
- `git switch -c name` is the command you will use most — create and switch
- Older syntax `git checkout -b name` does the same thing
- Your working directory changes to reflect that branch's files
- Uncommitted changes will come with you — commit or stash first
- `git branch` after switching confirms which branch you are on

## When I use this
Starting any new piece of work — immediately create and switch
to a new branch before making any changes.
