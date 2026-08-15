# tree — Visualize Directory Structure

## What it does
Prints the folder hierarchy as a visual tree — much clearer than repeated ls calls.

## Syntax
```bash
tree practice
tree -L 2 practice     # limit depth to 2 levels
```

## My Terminal Output
```bash
rushi@rushi:~$ tree ~/practice
/home/rushi/practice
├── configs
├── logs
│   ├── access.log
│   ├── app.log
│   └── error.log
└── scripts
```

## Install if missing
```bash
sudo apt install tree
```

## Key Points
- `-L 2` limits how many levels deep it goes — useful for large projects
- If tree is not installed use `ls -R` as an alternative

## When I use this
After setting up a project structure to confirm everything looks right.
