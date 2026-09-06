# Fixing a Rejected Push — Remote Has New Commits

## What it is
When someone else (or you from another machine) pushed to GitHub
before you, your push gets rejected to protect their work.

## The Error
```bash
rushi@rushi:~/Cloud-Devops$ git push
To git@github.com:DevRushi-engg/Cloud-Devops.git
 ! [rejected] main -> main (fetch first)
error: failed to push some refs
hint: Updates were rejected because the remote contains work
hint: you do not have locally.
```

## The Fix
```bash
# step 1 — bring their changes in first
git pull

# step 2 — resolve any conflicts if they appear
# edit conflicting files, then:
git add .
git commit -m "fix: resolve merge conflict"

# step 3 — push now
git push
```

## Key Points
- This is Git protecting your teammates' work — not a bug
- NEVER use `git push --force` on a shared branch — it erases their commits
- `--force` is only ever safe on your own private branch that nobody else uses
- Pull first, push last — the golden habit that prevents this entirely
- If a conflict appears during pull, resolve it the same way as a merge conflict

## Prevention
```bash
# start every session with this
git pull

# then do your work and push at the end
git push
```

## When I use this
Any time my push is rejected — pull first, then push.
