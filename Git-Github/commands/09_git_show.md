# git show — Inspect a Specific Commit

## What it does
Displays the commit message and the exact changes made
in a specific commit.

## Syntax
```bash
git show                    # the most recent commit
git show a1b2c3d            # a specific commit by hash
git show HEAD               # same as the most recent
git show HEAD~1             # one commit before the latest
```

## My Terminal Output
```bash
rushi@rushi:~/myproject$ git show --stat
commit c696b11 (HEAD -> main)
Author: Rushikesh <rushi@example.com>
Date:   Mon Aug 11 10:00:00 2026

    fix: resolve README merge conflict

 README.md | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

## Key Points
- Get the hash from `git log --oneline`
- Only the first 7 characters of the hash are needed
- `HEAD` always means your most recent commit
- `HEAD~1` means one before HEAD, `HEAD~2` means two before, and so on
- Press `q` to exit

## When I use this
Reviewing what a past commit actually changed, finding when
a specific line was introduced.
