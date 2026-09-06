# git clone — Copy an Existing Repository

## What it does
Downloads a complete repository from GitHub to your machine —
including all commits, branches, and history.
Sets up `origin` automatically — no `git remote add` needed.

## Syntax
```bash
git clone git@github.com:user/project.git         # clone into folder named 'project'
git clone git@github.com:user/project.git myfolder # clone into custom folder name
git clone https://github.com/user/project.git      # HTTPS version
```

## My Terminal Output
```bash
rushi@rushi:~$ git clone git@github.com:DevRushi-engg/Cloud-Devops.git
Cloning into 'Cloud-Devops'...
remote: Enumerating objects: 45, done.
remote: Counting objects: 100% (45/45), done.
Receiving objects: 100% (45/45), 12.5 KiB | 2.5 MiB/s, done.

rushi@rushi:~$ cd Cloud-Devops
rushi@rushi:~/Cloud-Devops$ git remote -v
origin  git@github.com:DevRushi-engg/Cloud-Devops.git (fetch)
origin  git@github.com:DevRushi-engg/Cloud-Devops.git (push)
```

## init vs clone
| Situation | Command |
|-----------|---------|
| Brand new project, nothing on GitHub | `git init` then push |
| Project already on GitHub, nothing local | `git clone` |
| Joining an existing team project | `git clone` |
| Code already local, nothing on GitHub | `git init` and push |

## Key Points
- `clone` sets up `origin` automatically — no extra steps
- Never run `git init` inside a cloned repo — it already is one
- The cloned folder name matches the repo name by default
- You get the full history — not just the latest files
- Use SSH URL if you set up SSH keys, HTTPS otherwise

## When I use this
Starting work on any existing project — open source contribution,
joining a team, or working on a second machine.
