# git stash — Park Unfinished Work Temporarily

## What it does
Saves your uncommitted changes to a temporary shelf and cleans
your working directory instantly. Lets you switch context
without committing half-finished work.

## Syntax
```bash
git stash                    # save current changes
git stash list               # see what is parked
git stash pop                # restore and remove from stash
git stash apply              # restore but keep in stash
git stash drop               # delete the stash without restoring
git stash -m "wip: login"    # save with a descriptive name
```

## My Terminal Output
```bash
# mid-feature, urgent bug arrives
rushi@rushi:~/Cloud-Devops$ git status
Changes not staged for commit:
        modified: README.md

rushi@rushi:~/Cloud-Devops$ git stash
Saved working directory and index state WIP on feature-login

rushi@rushi:~/Cloud-Devops$ git status
nothing to commit, working tree clean

# fix the bug, then come back
rushi@rushi:~/Cloud-Devops$ git stash pop
On branch feature-login
Changes not staged for commit:
        modified: README.md
Dropped refs/stash@{0}
```

## The classic stash moment
```bash
# you are mid-feature and an urgent bug arrives
git stash                                    # park your work
git switch main && git switch -c hotfix      # work on the fix
# fix, commit, push, open PR
git switch feature-login                     # return to feature
git stash pop                                # restore your work
```

## stash pop vs stash apply
| Command | What it does |
|---------|-------------|
| `stash pop` | Restores AND removes from stash list |
| `stash apply` | Restores but KEEPS in stash list |

## Key Points
- Stash is a shelf, not a commit — do not leave work there for days
- `stash list` shows `stash@{0}`, `stash@{1}` etc — newest first
- `stash pop` takes the most recent stash by default
- Can cause a conflict when popping if the branch changed meanwhile
- Works on both staged and unstaged changes

## When I use this
When an urgent bug or review request comes in while I am
mid-feature and not ready to commit yet.
