# git blame — Who Changed Each Line and When

## What it does
Shows for every line in a file: who last changed it,
when they changed it, and which commit made the change.

## Syntax
```bash
git blame README.md                  # blame whole file
git blame -L 10,20 README.md         # lines 10 to 20 only
git blame --since="2 weeks ago" file # recent changes only
```

## My Terminal Output
```bash
rushi@rushi:~/Cloud-Devops$ git blame README.md
c696b11 (Rushikesh 2026-08-11 10:00:00 +0530  1) # Cloud-Devops
c696b11 (Rushikesh 2026-08-11 10:00:00 +0530  2) Documenting my journey
a1b2c3d (Rushikesh 2026-08-12 09:00:00 +0530  3) through the cohort.
```

## Reading the output
```
c696b11  (Rushikesh  2026-08-11  1) # Cloud-Devops
   │          │           │      │       │
 commit    author       date   line   content
```

## Key Points
- `git blame` is for understanding code history, not for blame
- Combined with `git show <hash>` you can see the full context
- `-L` limits output to specific lines — useful for large files
- On GitHub, click any line number then "View git blame" for a visual version
- The name comes from "who do I blame for this code" — but use it kindly

## When I use this
Finding when a bug was introduced, understanding why a line
exists, or finding the original author to ask questions.
