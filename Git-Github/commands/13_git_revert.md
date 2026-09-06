# git revert — Safely Undo a Past Commit

## What it does
Creates a NEW commit that reverses the changes from a past commit.
The original commit stays in history — nothing is destroyed.
The safe way to undo work that has already been shared.

## Syntax
```bash
git revert a1b2c3d              # undo a specific commit
git revert HEAD                 # undo the most recent commit
git revert HEAD --no-edit       # skip the editor prompt
```

## My Terminal Output
```bash
rushi@rushi:~/myproject$ git log --oneline
c3d4e5f Add broken feature
b2c3d4e Add README

rushi@rushi:~/myproject$ git revert c3d4e5f
[main d4e5f6a] Revert "Add broken feature"
 1 file changed, 1 deletion(-)

rushi@rushi:~/myproject$ git log --oneline
d4e5f6a Revert "Add broken feature"
c3d4e5f Add broken feature
b2c3d4e Add README
# original commit still there, new revert commit added
```

## revert vs reset
| | `git revert` | `git reset` |
|-|-------------|------------|
| History | Preserved — adds new commit | Rewritten — old commits gone |
| Safe for shared branches | ✅ Yes | ❌ No |
| Use case | Undo pushed work | Local cleanup only |

## Key Points
- `revert` is always safe — it never deletes history
- `reset` rewrites history — only for local work you have not pushed
- An editor opens for the revert commit message — save and close it
- `--no-edit` skips the editor and uses the default message
- Use the hash from `git log --oneline`

## When I use this
Undoing a commit that has already been pushed to GitHub — the
only safe option in that case.
