# chown — Change File Ownership

## What it does
Changes who owns a file or folder, and which group it belongs to.

## Syntax
```bash
sudo chown user report.txt           # change owner only
sudo chown user:devs report.txt      # change owner and group
sudo chown -R user:devs project/     # apply to whole folder tree
```

## My Terminal Output
```bash
rushi@rushi:~$ ls -l report.txt
-rw-r--r-- 1 root root 512 Aug 11 report.txt

rushi@rushi:~$ sudo chown rushi:rushi report.txt
rushi@rushi:~$ ls -l report.txt
-rw-r--r-- 1 rushi rushi 512 Aug 11 report.txt
```

## Flags
| Flag | What it does |
|------|-------------|
| `user:group` | Changes both owner and group at once |
| `-R` | Applies recursively through a whole folder tree |

## Key Points
- Almost always needs `sudo` — you are changing ownership
- `user:group` format changes both in one command
- `-R` is essential when fixing permissions on a whole project folder
- Check current ownership first with `ls -l`

## When I use this
After copying files as root, fixing permission errors on web server directories, or setting up shared project folders.
