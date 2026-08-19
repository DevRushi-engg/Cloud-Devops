# sed — Stream Editor, Find and Replace

## What it does
Transforms text as it streams through — find and replace,
delete lines, and more — without opening an editor.

## Syntax
```bash
sed 's/foo/bar/' file.txt       # replace first match per line
sed 's/foo/bar/g' file.txt      # replace every match per line
sed -i 's/foo/bar/g' file.txt   # edit the file in place
sed -i.bak 's/foo/bar/g' file   # edit in place, keep backup
```

## My Terminal Output
```bash
rushi@rushi:~$ cat notes.txt
hello foo world foo

rushi@rushi:~$ sed 's/foo/bar/' notes.txt
hello bar world foo

rushi@rushi:~$ sed 's/foo/bar/g' notes.txt
hello bar world bar

rushi@rushi:~$ sed -i 's/foo/bar/g' notes.txt
rushi@rushi:~$ cat notes.txt
hello bar world bar
```

## The Substitution Pattern
```
s/old/new/
│  │   │
│  │   └── replacement text
│  └────── pattern to find
└────────── s means substitute
```
Add `g` at the end to replace ALL occurrences on each line.

## Key Points
- Without `g`, only the first match per line is replaced
- `-i` edits the actual file — use carefully, changes are permanent
- `-i.bak` makes a backup before editing — safer habit
- Works on piped input too: `cat file | sed 's/old/new/g'`

## When I use this
Bulk replacing config values, updating URLs across files,
cleaning up log output before further processing.
