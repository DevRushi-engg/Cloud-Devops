# git remote set-url — Fix or Change Remote URL

## What it does
Updates where `origin` points — fixing a wrong URL or switching
from HTTPS to SSH without removing and re-adding the remote.

## Syntax
```bash
git remote set-url origin git@github.com:user/repo.git    # fix URL
git remote -v                                              # verify
```

## My Terminal Output
```bash
# wrong HTTPS URL was set
rushi@rushi:~/Cloud-Devops$ git remote -v
origin  https://github.com/DevRushi-engg/Cloud-Devops.git (fetch)
origin  https://github.com/DevRushi-engg/Cloud-Devops.git (push)

# fix it to SSH
rushi@rushi:~/Cloud-Devops$ git remote set-url origin git@github.com:DevRushi-engg/Cloud-Devops.git

rushi@rushi:~/Cloud-Devops$ git remote -v
origin  git@github.com:DevRushi-engg/Cloud-Devops.git (fetch)
origin  git@github.com:DevRushi-engg/Cloud-Devops.git (push)
```

## Common scenarios
| Situation | Command |
|-----------|---------|
| Wrong repo URL | `git remote set-url origin <correct-url>` |
| Switch HTTPS to SSH | `git remote set-url origin git@github.com:user/repo.git` |
| Repo was renamed | `git remote set-url origin <new-url>` |

## Key Points
- Always run `git remote -v` after to confirm the change
- Copy the exact URL from your GitHub repo page
- SSH URL format: `git@github.com:username/reponame.git`
- HTTPS URL format: `https://github.com/username/reponame.git`

## When I use this
When a push fails due to wrong URL, or when switching from
HTTPS to SSH authentication after setting up SSH keys.
