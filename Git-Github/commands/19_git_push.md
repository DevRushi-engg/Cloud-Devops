# git push — Send Commits to GitHub

## What it does
Uploads your local commits to the remote repository on GitHub.
Nothing is on GitHub until you push — committing is local only.

## Syntax
```bash
git push -u origin main        # first push — sets upstream
git push                       # every push after that
git push -u origin feature-login   # push a new branch
git push origin --delete feature-login  # delete remote branch
```

## My Terminal Output
```bash
rushi@rushi:~/Cloud-Devops$ git push -u origin main
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 16 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (9/9), 1.15 KiB | 1.15 MiB/s, done.
Total 9 (delta 1), reused 0 (delta 0)
To git@github.com:DevRushi-engg/Cloud-Devops.git
   ef30bf0..c696b11  main -> main
branch 'main' set up to track 'origin/main'.

rushi@rushi:~/Cloud-Devops$ git push
Everything up-to-date
```

## Key Points
- `-u` sets the upstream — links your local branch to the remote branch
- After `-u` once, plain `git push` is enough forever
- Committing is local — only pushing makes work visible to others
- Push often — it is your backup
- Never use `--force` on a shared branch — it can erase teammates' commits

## When push is rejected
```bash
# someone else pushed before you
git pull           # bring their changes in first
# resolve any conflicts
git push           # then push yours
```

## When I use this
At the end of every working session and after every meaningful
commit — pushing keeps GitHub in sync and work backed up.


