# date & cal — Time and Calendar

## What it does
`date` shows the current date and time. `cal` prints a calendar.

## Syntax
```bash
date                  # current date and time
cal                   # calendar for current month
date +%Y-%m-%d        # custom format — great for filenames
```

## My Terminal Output
```bash
rushi@rushi:~$ date
Sat Aug 11 10:35:22 IST 2026

rushi@rushi:~$ date +%Y-%m-%d
2026-08-11
```

## Key Points
- `date +FORMAT` is very useful for creating timestamped filenames in scripts
- `%Y` = year, `%m` = month, `%d` = day, `%H` = hour, `%M` = minute

## When I use this
For timestamped log filenames and checking server time during troubleshooting.
