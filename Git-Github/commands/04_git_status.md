# git status — See What Has Changed

## What it does
Shows which files are untracked, modified, or staged.
Your most-used Git command — run it constantly.

## Syntax
```bash
git status
```

## My Terminal Output
```bash
rushi@rushi:~/myproject$ git status
On branch main

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        notes.txt
        README.md

nothing added to commit but untracked files present

rushi@rushi:~/myproject$ git add README.md
rushi@rushi:~/myproject$ git status
On branch main

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        new file: README.md

Untracked files:
        notes.txt
```

## Reading the output
| Section | Meaning |
|---------|---------|
| `Untracked files` | New files Git has never seen |
| `Changes not staged` | Modified tracked files not yet added |
| `Changes to be committed` | Staged — ready for commit |

## Key Points
- Run `git status` before AND after every command when learning
- It always suggests the next command you probably want
- When confused about Git, this is always the first thing to run
- Green = staged, Red = not staged

## When I use this
Before every `git add` and `git commit` — constantly throughout
every working session.
