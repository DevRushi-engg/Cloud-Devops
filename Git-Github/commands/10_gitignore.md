# .gitignore — Files Git Should Never Track

## What it does
Tells Git to completely ignore certain files and folders —
secrets, build output, logs, and editor temp files.

## Create the file
```bash
nano .gitignore
git add .gitignore
git commit -m "Add gitignore"
```

## Common .gitignore contents
```bash
# secrets and environment
.env
*.pem
*.key
secrets/

# logs
*.log
logs/

# build output
node_modules/
__pycache__/
*.pyc
dist/
build/

# editor temp files
.vscode/
.idea/
*.swp

# OS files
.DS_Store
Thumbs.db
```

## My Terminal Output
```bash
rushi@rushi:~/myproject$ cat .gitignore
.env
*.log
node_modules/

rushi@rushi:~/myproject$ touch secrets.env
rushi@rushi:~/myproject$ git status
On branch main
nothing to commit, working tree clean
# secrets.env is not shown — gitignore is working
```

## Key Points
- `.gitignore` only works on files NOT already tracked
- Ignore BEFORE you `git add` — not after
- Never commit passwords, API keys, or `.env` files
- Add `.gitignore` to the repo itself so teammates get the same rules
- Use `git rm --cached filename` to untrack a file already committed

## ⚠️ Critical rule
If you accidentally commit a secret — change the secret immediately.
Removing it from Git history is complex and the old commit is still
accessible to anyone who cloned the repo.

## When I use this
Every new project — `.gitignore` is one of the first files I create
right after `git init`.
