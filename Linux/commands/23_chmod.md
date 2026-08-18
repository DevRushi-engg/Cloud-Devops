# chmod — Change File Permissions

## What it does
Sets who can read, write, or execute a file.
Works in two modes: symbolic (letters) or octal (numbers).

## Syntax — Symbolic Mode
```bash
chmod u+x script.sh      # give owner execute permission
chmod o-w notes.txt      # remove write from others
chmod a+r report.txt     # read for everyone
chmod g+rw shared.txt    # give group read and write
```

## Syntax — Octal Mode
```bash
chmod 755 script.sh      # owner=rwx, group=rx, others=rx
chmod 644 notes.txt      # owner=rw, group=r, others=r
chmod 600 secret.conf    # owner=rw only, completely private
chmod 700 secret/        # owner only, full access
```

## My Terminal Output
```bash
rushi@rushi:~/project$ chmod 755 bin/run.sh
rushi@rushi:~/project$ ls -l bin/
-rwxr-xr-x 1 rushi rushi 12 Aug 11 run.sh

rushi@rushi:~/project$ chmod 600 config/app.conf
rushi@rushi:~/project$ ls -l config/
-rw------- 1 rushi rushi 11 Aug 11 app.conf
```

## Understanding Octal Numbers
| Number | Permission | Calculation |
|--------|-----------|-------------|
| 7 | rwx | 4+2+1 |
| 6 | rw- | 4+2 |
| 5 | r-x | 4+1 |
| 4 | r-- | 4 |
| 0 | --- | none |

Three digits = owner, group, others → `chmod 755` = `rwx r-x r-x`

## Symbolic Mode Reference
| Who | Meaning |
|-----|---------|
| `u` | owner (user) |
| `g` | group |
| `o` | others |
| `a` | all three |

## Memorize just two
- `644` → regular files (owner edits, everyone reads)
- `755` → scripts and folders (owner runs, everyone can enter/read)

## When I use this
Making a script executable, locking down a config file, setting up shared folder permissions.

