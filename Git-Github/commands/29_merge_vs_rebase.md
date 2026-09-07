# Merge vs Rebase — Two Ways to Join Branches

## What it is
When two branches have diverged, you must choose how to
rejoin them. Merge keeps the full history. Rebase rewrites it.

## Merge
```bash
git switch main
git merge feature-login
```
```
Before:           After merge:
main:    A─B─C    A─B─C─────M
feature:   B─D─E        D─E─┘
```
Keeps both lines of history plus adds a merge commit (M).
Truthful — shows exactly what happened.

## Rebase
```bash
git switch feature-login
git rebase main
```
```
Before:           After rebase:
main:    A─B─C    A─B─C─D'─E'
feature:   B─D─E
```
Replays your commits on top of main. One clean straight line.
Rewrites commit IDs — D becomes D', E becomes E'.

## Comparison
| | Merge | Rebase |
|-|-------|--------|
| History | Keeps both, adds merge commit | One straight line |
| Truthful | Yes — shows what happened | No — rewrites commits |
| Safe on shared branch | ✅ Always | ❌ Dangerous if pushed |
| Use when | Default — team branches | Cleaning up own local work |

## Key Points
- When in doubt, always merge — it is always safe
- Never rebase commits you have already pushed and shared
- `git rebase --abort` backs out safely at any point
- The golden rule: **rewrite freely before you push, never after**

## When I use this
Merge for everything on shared branches.
Rebase only to clean up my own local feature branch before
opening a PR — never after pushing.

