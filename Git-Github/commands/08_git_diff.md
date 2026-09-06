# git diff — See Exactly What Changed

## What it does
Shows the actual line-by-line differences between versions.
Review changes before staging or committing.

## Syntax
```bash
git diff                    # changes not yet staged
git diff --staged           # changes staged but not committed
git diff a1b2c3d            # compare to a specific commit
git diff main feature-login # compare two branches
```

## My Terminal Output
```bash
rushi@rushi:~/myproject$ git diff
diff --git a/notes.txt b/notes.txt
index e69de29..a1b2c3d 100644
--- a/notes.txt
+++ b/notes.txt
@@ -0,0 +1,2 @@
+# My Notes
+Learning Git today
```

## Reading the diff
```
--- a/notes.txt    old version
+++ b/notes.txt    new version
-removed line      shown in red
+added line        shown in green
```

## Key Points
- `git diff` with no arguments shows unstaged changes only
- `git diff --staged` shows what will be included in the next commit
- Review with `git diff --staged` before every commit — good habit
- Press `q` to quit the diff view
- No output means no changes

## When I use this
Before staging to see what I changed, before committing to confirm
the staged changes look right.
