# cron & crontab — Schedule Scripts to Run Automatically

## What it does
Runs commands or scripts on a schedule — while you sleep,
every hour, every day, whatever you configure.

## Syntax
```bash
crontab -e      # edit your cron jobs
crontab -l      # list your current jobs
crontab -r      # remove all your cron jobs
```

## Cron schedule format
```
* * * * * command
│ │ │ │ │
│ │ │ │ └── day of week (0-7, 0 and 7 = Sunday)
│ │ │ └──── month (1-12)
│ │ └────── day of month (1-31)
│ └──────── hour (0-23)
└────────── minute (0-59)
```

## Common schedule examples
```bash
# every day at 2am
0 2 * * * ~/backup.sh

# every 5 minutes
*/5 * * * * ~/health.sh

# every hour
0 * * * * ~/check.sh

# every Monday at 9am
0 9 * * 1 ~/weekly_report.sh

# every day at midnight
0 0 * * * ~/daily.sh
```

## My Terminal Output
```bash
rushi@rushi:~$ crontab -e
# editor opens, add your line, save and exit

rushi@rushi:~$ crontab -l
*/5 * * * * ~/health.sh
0 2 * * * ~/backup.sh
```

## Key Points
- `*` means "every" — `* * * * *` runs every single minute
- `*/5` means "every 5" — works for any field
- Use full paths in cron — cron has a minimal environment
- Redirect output to a log: `~/script.sh >> ~/script.log 2>&1`
- Test your script manually before scheduling it
- Use https://crontab.guru to check your schedule expression

## When I use this
Scheduling backups, health checks, log rotation, and any task
that should run automatically on a timer.
