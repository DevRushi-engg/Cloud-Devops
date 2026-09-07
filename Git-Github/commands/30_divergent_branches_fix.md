# Divergent Branches — Fixing the Split History Error

## What it is
When both your local repo and the remote have commits the
other does not have, Git refuses to push and asks you to choose
how to reconcile the split histories.

## The Error
```bash
rushi@rushi:~/Cloud-Devops$ git pull
hint: You have divergent branches and need to specify how
hint: to reconcile them.
hint:   git config pull.rebase false  # merge
hint:   git config pull.rebase true   # rebase
fatal: Need to specify how to reconcile divergent branches.
```

## The Fix — Step by Step
```bash
# step 1 — tell Git to use merge strategy (do this once)
git config pull.rebase false

# step 2 — pull and join the histories
git pull origin main --allow-unrelated-histories

# step 3 — if a conflict appears, resolve it
# edit the conflicting file, remove markers, then:
git add README.md
git commit -m "fix: resolve merge conflict"

# step 4 — push
git push -u origin main
```

## My Terminal Output
```bash
rushi@rushi:~/Cloud-Devops$ git config pull.rebase false
rushi@rushi:~/Cloud-Devops$ git pull origin main --allow-unrelated-histories
From github.com:DevRushi-engg/Cloud-Devops
 * branch  main -> FETCH_HEAD
Merge made by the 'ort' strategy.

rushi@rushi:~/Cloud-Devops$ git push -u origin main
   ef30bf0..c696b11  main -> main
```

## Key Points
- `--allow-unrelated-histories` is only needed when joining two
  completely separate repos for the first time
- `git config pull.rebase false` sets merge as the default strategy
  globally — run this once per machine
- This is exactly what happened on Day 2 — now you know why each line exists
- Every error Git shows has a hint — always read the hint first

## When I use this
When a fresh `git pull` fails with the divergent branches error —
usually when the remote was initialized with a README while
the local repo was initialized separately.

