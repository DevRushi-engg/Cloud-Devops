# Git Install & Configuration — First Time Setup

## What it does
Installs Git and configures your identity so every commit
is stamped with your name and email.

## Install
```bash
sudo apt update && sudo apt install -y git
git --version                    # confirm install
```

## Configure (do this once per machine)
```bash
git config --global user.name "Rushikesh"
git config --global user.email "you@example.com"
git config --global core.editor nano    # set default editor
git config --list                        # check all settings
```

## My Terminal Output
```bash
rushi@rushi:~$ git --version
git version 2.43.0

rushi@rushi:~$ git config --global user.name "Rushikesh"
rushi@rushi:~$ git config --global user.email "rushi@example.com"
rushi@rushi:~$ git config --list
user.name=Rushikesh
user.email=rushi@example.com
core.editor=nano
```

## Key Points
- `--global` sets it for every project on this machine
- Use the same email as your GitHub account — links commits to your profile
- Without this Git will refuse to commit or stamp the wrong author
- Settings are stored in `~/.gitconfig`
- You only do this once per machine

## When I use this
First thing after installing Git on any new machine or VM.
