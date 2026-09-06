# git pull — Bring Remote Changes Down

## What it does
Downloads new commits from GitHub and merges them into
your current branch. Keeps you in sync with your team.

## Syntax
```bash
git pull                        # fetch + merge from origin
git pull origin main            # explicit branch
git fetch                       # download only, do not merge
git fetch origin                # fetch all remote changes
```

## My Terminal Output
```bash
rushi@rushi:~/Cloud-Devops$ git pull
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
Unpacking objects: 100% (3/3), done.
From git@github.com:DevRushi-engg/Cloud-Devops
   c696b11..d4e5f6a  main -> origin/main
Updating c696b11..d4e5f6a
Fast-forward
 README.md | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)

rushi@rushi:~/Cloud-Devops$ git pull
Already up to date.
```

## fetch vs pull
| | `git fetch` | `git pull` |
|-|------------|-----------|
| Downloads changes | ✅ Yes | ✅ Yes |
| Merges into branch | ❌ No | ✅ Yes |
| Safe to run anytime | ✅ Yes | Mostly yes |
| Use case | Look before merging | Day to day sync |

`git pull` = `git fetch` + `git merge` in one step.

## Key Points
- Pull before you start work every day — builds on latest version
- Pull before pushing if your push gets rejected
- Can cause a merge conflict — that is normal, resolve and commit
- `git fetch` lets you inspect changes before applying them
- Golden habit: **pull before you start, push when you finish**

## When I use this
First thing every morning before starting work, and whenever
my push gets rejected because the remote has new commits.

