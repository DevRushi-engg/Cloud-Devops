# git commit — Save a Permanent Snapshot

## What it does
Permanently records everything in the Staging Area into the
repository with a message explaining what changed and why.

## Syntax
```bash
git commit -m "Add project README"          # commit with message
git commit -am "Fix typo in notes"          # stage tracked + commit
git commit --amend -m "Better message"      # fix last commit
```

## My Terminal Output
```bash
rushi@rushi:~/myproject$ git add README.md
rushi@rushi:~/myproject$ git commit -m "Add README with project title"
[main (root-commit) a1b2c3d] Add README with project title
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
```

## Good commit messages
| Instead of | Write |
|-----------|-------|
| `"stuff"` | `"Add user login validation"` |
| `"fixed it"` | `"Fix crash when email field is empty"` |
| `"update"` | `"Update README with setup steps"` |
| `"asdf"` | `"Remove unused imports from app.py"` |

Complete this sentence: *"If applied, this commit will..."*
Use present tense. Keep it under 72 characters.

## Key Points
- Every commit gets a unique hash ID like `a1b2c3d`
- The message is permanent — make it meaningful
- `-am` stages all TRACKED files and commits in one step
- `-am` does NOT include brand new untracked files — `git add` those first
- Never amend a commit you have already pushed to a shared branch

## Commit message convention used in this repo
```
init: first setup
docs: add pwd command notes
lab: linux directory tree exercise
fix: correct ls flags explanation
feat: add health check script
```

## When I use this
After staging changes — saving a logical unit of work with
a clear message about what changed and why.
