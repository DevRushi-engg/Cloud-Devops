# git restore — Undo Changes Safely

## What it does
Two modes:
- Unstage a file (keep your edits)
- Discard edits entirely (back to last commit)

## Syntax
```bash
# unstage — removes from staging, keeps your edits
git restore --staged notes.txt

# discard edits — reverts file to last committed version
git restore notes.txt

# older syntax (still works)
git reset HEAD notes.txt        # unstage
git checkout -- notes.txt       # discard edits
```

## My Terminal Output
```bash
# unstage example
rushi@rushi:~/myproject$ git add secret.txt
rushi@rushi:~/myproject$ git status
Changes to be committed:
        new file: secret.txt

rushi@rushi:~/myproject$ git restore --staged secret.txt
rushi@rushi:~/myproject$ git status
Untracked files:
        secret.txt
# file is out of staging, edits still there

# discard edits example
rushi@rushi:~/myproject$ echo "bad change" >> notes.txt
rushi@rushi:~/myproject$ git restore notes.txt
# notes.txt is back to its last committed state
```

## ⚠️ Warning
```bash
git restore notes.txt    # PERMANENT — no undo
```
Your uncommitted edits are gone forever.
Use when an experiment went wrong and you want a clean slate.

## Key Points
- `--staged` is safe — your edits survive, file just moves back to working dir
- Without `--staged` it is destructive — use with care
- `git status` tells you these commands — it suggests them in its output
- When in doubt, use `--staged` first

## When I use this
`--staged` when I accidentally added the wrong file.
Without `--staged` when I want to throw away a bad experiment.

