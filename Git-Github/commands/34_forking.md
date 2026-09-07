# Forking — Contributing to Code You Do Not Own

## What it is
A fork is your own personal copy of someone else's repository
on your GitHub account. You can push freely to your fork.
Then open a PR from your fork back to their original repo.

## When to fork vs branch
| Situation | Use |
|-----------|-----|
| You are on the team, have write access | Branch |
| Contributing to a stranger's open source project | Fork |
| Want your own copy to experiment with | Fork |
| Working on your own repo | Branch |

## The open source contribution workflow
```bash
# 1. click Fork on their GitHub repo page
# 2. clone YOUR fork
git clone git@github.com:DevRushi-engg/their-repo.git

# 3. branch, make your change, commit
git switch -c fix-typo
# edit the file
git add .
git commit -m "fix: correct typo in README"

# 4. push to YOUR fork
git push -u origin fix-typo

# 5. on GitHub — open a PR from your fork to their original repo
# "Compare & pull request" → base: their repo, head: your fork
```

## Keeping your fork up to date
```bash
# add their original repo as 'upstream' — do this once
git remote add upstream git@github.com:them/their-repo.git

# fetch their latest changes
git fetch upstream

# merge into your local main
git merge upstream/main

# push to keep your fork in sync
git push
```

## Two remotes explained
| Remote | Points to |
|--------|-----------|
| `origin` | YOUR fork on GitHub |
| `upstream` | Their ORIGINAL repo |

## Key Points
- Fork when you do not have write access to the repo
- Always sync from upstream before starting new work
- Your fork is completely independent — you can break it freely
- The PR goes from your fork's branch to their main branch
- Open source projects often have contribution guidelines (CONTRIBUTING.md)

## When I use this
Contributing to public GitHub repositories, open source projects,
or any repo I do not have write access to.
