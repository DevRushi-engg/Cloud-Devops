# Variables — Store and Reuse Values in Scripts

## What it does
Variables store values so you can reuse them throughout a script.
Assign once, reference anywhere.

## Syntax
```bash
name="Rushi"               # assign — no spaces around =
echo "Hello, $name"        # read with $
echo "Hello, ${name}"      # safer with braces
count=5                    # numbers are still text
```

## My Terminal Output
```bash
rushi@rushi:~$ name="Rushi"
rushi@rushi:~$ echo "Hello, $name"
Hello, Rushi

rushi@rushi:~$ greeting="Good morning"
rushi@rushi:~$ echo "$greeting, $name"
Good morning, Rushi
```

## Key Points
- NO spaces around `=` — `name = "Rushi"` will error
- Read a variable with `$name` or `${name}`
- Always wrap in double quotes: `"$name"` — handles spaces safely
- Everything is text by default unless you do arithmetic
- Variable names are case sensitive — `Name` and `name` are different

## Special variables in scripts
| Variable | Meaning |
|----------|---------|
| `$1 $2 $3` | Arguments passed to the script |
| `$@` | All arguments |
| `$#` | Number of arguments |
| `$0` | The script's own name |
| `$?` | Exit code of last command |

## When I use this
Storing file paths, usernames, timestamps — anything you reference
more than once in a script.

