# git log — See the Commit History

## What it does
Lists every commit in the repository, newest first.
Shows the hash, author, date, and message for each commit.

## Syntax
```bash
git log                          # full detail
git log --oneline                # compact one line each
git log --oneline --graph        # with branch visualization
git log --oneline -5             # last 5 commits only
git log --author="Rushikesh"     # filter by author
```

## My Terminal Output
```bash
rushi@rushi:~/myproject$ git log --oneline
c696b11 fix: resolve README merge conflict
496f80e init: project structure and README
ef30bf0 Initial commit

rushi@rushi:~/myproject$ git log --oneline --graph
* c696b11 fix: resolve README merge conflict
* 496f80e init: project structure and README
* ef30bf0 Initial commit
```

## Full log output
```bash
commit c696b11a2f3d4e5f6a7b8c9d0e1f2a3b4c5d6e7f
Author: Rushikesh <rushi@example.com>
Date:   Mon Aug 11 10:00:00 2026 +0530

    fix: resolve README merge conflict
```

## Key Points
- Press `q` to quit the log view
- `--oneline` is what you will use 90% of the time — much easier to read
- The short hash (first 7 characters) is enough to reference a commit
- `--graph` shows branches splitting and merging visually
- Newest commit is always at the top

## When I use this
Checking what changed recently, finding a commit hash to revert,
reviewing the project history before making changes.

