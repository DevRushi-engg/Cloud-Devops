# git remote — Link Local Repo to GitHub

## What it does
Connects your local repository to a remote repository on GitHub.
`origin` is the conventional name for your main remote.

## Syntax
```bash
git remote add origin git@github.com:username/repo.git   # add remote
git remote -v                                             # check it
git remote remove origin                                  # remove it
git remote set-url origin git@github.com:user/new.git    # fix wrong URL
```

## My Terminal Output
```bash
rushi@rushi:~/Cloud-Devops$ git remote add origin git@github.com:DevRushi-engg/Cloud-Devops.git

rushi@rushi:~/Cloud-Devops$ git remote -v
origin  git@github.com:DevRushi-engg/Cloud-Devops.git (fetch)
origin  git@github.com:DevRushi-engg/Cloud-Devops.git (push)
```

## Key Points
- `origin` is just a name — convention, not a requirement
- `-v` shows both fetch and push URLs — always verify after adding
- Copy the exact SSH URL from your GitHub repo page
- Use the SSH tab URL not the HTTPS one if you set up SSH keys
- You only run `git remote add` once per project
- If you get "remote origin already exists" use `git remote set-url`

## Common errors and fixes
| Error | Fix |
|-------|-----|
| `remote origin already exists` | `git remote set-url origin <new-url>` |
| `Permission denied (publickey)` | SSH key not added to GitHub |
| Wrong URL | `git remote set-url origin <correct-url>` |

## When I use this
Once per project — connecting a local repo to its GitHub home
for the first time.
