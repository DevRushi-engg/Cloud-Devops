# git add — Stage Changes for Commit

## What it does
Moves changes from the Working Directory into the Staging Area.
Nothing is saved permanently yet — you are just choosing
what goes into the next commit.

## Syntax
```bash
git add notes.txt                 # stage one file
git add file1.txt file2.txt       # stage several files
git add .                         # stage everything changed
git add *.md                      # stage all markdown files
git add Linux/                    # stage a whole folder
```

## My Terminal Output
```bash
rushi@rushi:~/myproject$ git status
Untracked files:
        README.md
        notes.txt

rushi@rushi:~/myproject$ git add README.md
rushi@rushi:~/myproject$ git status
Changes to be committed:
        new file: README.md

Untracked files:
        notes.txt
```

## Key Points
- `git add .` stages everything — convenient but check with `git status` first
- You can stage multiple rounds before committing once
- `git add` on a new file starts tracking it for the first time
- Staging is reversible — `git restore --staged file` unstages it
- `-am` in commit skips `git add` but ONLY for already tracked files
- Brand new files ALWAYS need `git add` first

## When I use this
After editing files and before every commit — choosing exactly
what snapshot I want to save.
