# if / else / elif — Conditionals in Shell Scripts

## What it does
Runs different commands depending on whether a condition is true or false.

## Syntax
```bash
if [ condition ]; then
    echo "true"
elif [ other condition ]; then
    echo "other"
else
    echo "false"
fi
```

## My Terminal Output
```bash
#!/bin/bash
name="Rushi"

if [ "$name" = "Rushi" ]; then
    echo "Welcome back, Rushi"
else
    echo "Who are you?"
fi
```
```
Welcome back, Rushi
```

## Comparison Tests
| Test | True when |
|------|-----------|
| `-eq` | Numbers are equal |
| `-ne` | Numbers are not equal |
| `-lt` | Number less than |
| `-gt` | Number greater than |
| `=` | Strings are equal |
| `!=` | Strings are not equal |
| `-z` | String is empty |
| `-n` | String is not empty |
| `-f` | Path exists and is a file |
| `-d` | Path exists and is a directory |
| `-e` | Path exists (file or folder) |

## Key Points
- Spaces inside `[ ]` are REQUIRED — `["$x"=1]` will error
- Use double quotes around variables: `"$name"` not `$name`
- Numbers use `-eq` `-lt` `-gt` — strings use `=` `!=`
- Mixing them is a classic bug
- `fi` closes the block — it is `if` spelled backwards

## When I use this
Checking if a service is running, if a file exists, if an argument
was passed — any decision point in a script.

