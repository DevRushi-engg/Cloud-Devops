# The Three Areas — Working Directory, Staging, Repository

## What it is
The mental model behind every Git operation.
Understanding these three areas explains every Git command.

## The Three Areas
```
Working Directory → Staging Area → Repository
   (your files)     (chosen changes)  (permanent history)
   where you edit   ready to save     committed snapshots
```

## How files move
```bash
# edit a file → it's in the Working Directory
nano notes.txt

# git add → moves it to Staging Area
git add notes.txt

# git commit → moves it to the Repository permanently
git commit -m "Add notes"
```

## Why Staging Exists
You edited 5 files but only 2 belong in this commit.
Staging lets you choose exactly what goes into each save point.

```
Edit freely → Stage deliberately → Commit with purpose
```

Think of staging as a box you are packing before you seal it.
You choose what goes in the box before you tape it shut.

## File States
| State | Meaning |
|-------|---------|
| Untracked | New file Git has never seen |
| Modified | Tracked file with unsaved changes |
| Staged | Ready to be committed |
| Committed | Permanently saved in history |

## Key Points
- `git add` moves from Working Directory → Staging
- `git commit` moves from Staging → Repository
- You can add, then add more, then commit all at once
- Nothing is permanent until `git commit`

## When I use this
This mental model is active every time I use Git — knowing
which area a file is in tells me exactly what command to run next.
