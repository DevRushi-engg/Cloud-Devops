# whoami & id — Who Am I?

## What it does
Shows information about the currently logged in user.

## Syntax
```bash
whoami
id
```

## My Terminal Output
```bash
rushi@rushi:~$ whoami
rushi

rushi@rushi:~$ id
uid=1000(rushi) gid=1000(rushi) groups=1000(rushi),4(adm),27(sudo)
```

## Key Points
- `whoami` prints just the username
- `id` shows user ID (uid), group ID (gid), and all groups you belong to
- Essential before running anything with `sudo` or dealing with permissions
- If you see `uid=0(root)` you are running as root — be careful

## When I use this
When troubleshooting permission errors, to confirm which user I am.
