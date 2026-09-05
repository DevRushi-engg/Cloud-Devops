# git init — Start Tracking a Folder

## What it does
Turns a regular folder into a Git repository by creating
a hidden `.git` folder inside it that stores the entire history.

## Syntax
```bash
git init                      # init in current folder
mkdir myproject && cd myproject && git init   # create and init
ls -a                         # confirm .git exists
```

## My Terminal Output
```bash
rushi@rushi:~$ mkdir myproject && cd myproject
rushi@rushi:~/myproject$ git init
Initialized empty Git repository in /home/rushi/myproject/.git/

rushi@rushi:~/myproject$ ls -a
.  ..  .git
```

## Key Points
- Run it once at the top of your project — never inside a subfolder
- The `.git` folder IS the repository — everything else is just your files
- Delete `.git` and it becomes an ordinary folder again
- Your files are not tracked yet — just the folder is initialized
- One project = one repo is the standard setup

## Git vs GitHub
| Git | GitHub |
|-----|--------|
| Tool on your machine | Website in the cloud |
| Tracks your changes | Hosts and shares repos |
| Works offline | Adds collaboration |

## When I use this
Starting any new project, or when I want to start tracking
an existing folder that has no version control yet.
