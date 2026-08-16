# file & stat — Inspect Files

## What it does
`file` identifies what a file actually is. `stat` shows detailed metadata.

## Syntax
```bash
file app.log
file photo.png
stat app.log
```

## My Terminal Output
```bash
rushi@rushi:~/practice$ file logs/app.log
logs/app.log: ASCII text

rushi@rushi:~/practice$ stat logs/app.log
  File: logs/app.log
  Size: 18        Blocks: 8    IO Block: 4096   regular file
  Access: 2026-08-11 10:02:00
  Modify: 2026-08-11 10:02:00
```

## Key Points
- `file` ignores the extension — it reads the actual file content
- `stat` shows three timestamps: Access, Modify, Change — useful for debugging scripts
- More detail than `ls -l` when you need it

## When I use this
`file` when I get a file with no extension. `stat` when debugging cron jobs or scripts.
