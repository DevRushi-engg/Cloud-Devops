# Exit Codes — How Commands Report Success or Failure

## What it does
Every command returns an exit code when it finishes.
`0` means success. Anything else means failure.
Scripts use exit codes to react to what happened.

## Syntax
```bash
ls /home
echo $?           # print last exit code

# react to success or failure
if ls /home; then
    echo "Command succeeded"
fi

# set your own exit code
exit 0    # success
exit 1    # failure
```

## My Terminal Output
```bash
rushi@rushi:~$ ls /home
rushi
rushi@rushi:~$ echo $?
0

rushi@rushi:~$ ls /nope
ls: cannot access '/nope': No such file or directory
rushi@rushi:~$ echo $?
2
```

## Common Exit Codes
| Code | Meaning |
|------|---------|
| `0` | Success |
| `1` | General error |
| `2` | Misuse of command |
| `126` | Permission denied |
| `127` | Command not found |

## Key Points
- `$?` holds the exit code of the LAST command run — read it immediately
- `0` = success, non-zero = something went wrong
- `if command; then` uses the exit code directly — cleaner than `$?`
- Use `exit 1` at the end of a script to signal failure to cron or a pipeline
- `&&` chains commands that only run if the previous succeeded
- `||` runs the next command only if the previous FAILED

## Practical pattern
```bash
# stop script on first error
set -e

# check and react
if ! curl -sI localhost | grep -q 200; then
    echo "Service is DOWN"
    exit 1
fi
```

## When I use this
Error handling in scripts — stopping when something fails,
logging whether a health check passed or failed.
