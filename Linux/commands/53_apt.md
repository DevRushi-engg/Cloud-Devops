# apt — Package Manager for Ubuntu and Debian

## What it does
Installs, removes, updates, and searches for software packages.
Handles all dependencies automatically — no manual hunting for files.

## Syntax
```bash
sudo apt update                  # refresh the package catalog
sudo apt upgrade                 # install available updates
sudo apt install nginx           # install a package
sudo apt install -y nginx        # install without yes/no prompt
sudo apt remove nginx            # uninstall, keep config
sudo apt purge nginx             # uninstall AND delete config
sudo apt autoremove              # clean orphaned dependencies
apt search nginx                 # find packages by keyword
apt show nginx                   # details about a package
dpkg -l | grep nginx             # check if installed
```

## My Terminal Output
```bash
rushi@rushi:~$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu jammy InRelease
Reading package lists... Done

rushi@rushi:~$ sudo apt install -y nginx
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed: nginx
Setting up nginx (1.18.0) ...

rushi@rushi:~$ dpkg -l | grep nginx
ii  nginx   1.18.0  amd64   small, powerful HTTP server
```

## update vs upgrade
| Command | What it does |
|---------|-------------|
| `apt update` | Refreshes the list of available packages — installs nothing |
| `apt upgrade` | Actually installs the newer versions |

Always run `update` before `install` — otherwise apt uses a stale catalog.

## remove vs purge
| Command | What it does |
|---------|-------------|
| `remove` | Uninstalls the package, keeps config files |
| `purge` | Uninstalls AND deletes all config files |

## Key Points
- `apt` is the high-level tool — `dpkg` is the low-level one it builds on
- `-y` skips the yes/no confirmation — useful in scripts
- `autoremove` after removing packages keeps the system clean
- Software comes from repositories — trusted online package libraries

## When I use this
Installing any new tool, keeping the server patched with updates,
cleaning up after removing a service.
