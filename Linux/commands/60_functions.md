# Functions — Reusable Blocks in Shell Scripts

## What it does
Groups commands into a named block you can call multiple times.
Keeps scripts organized and avoids repeating code.

## Syntax
```bash
# define
greet() {
    echo "Hello, $1"
}

# call it
greet "Rushi"
greet "Yash"
```

## My Terminal Output
```bash
#!/bin/bash

greet() {
    echo "Hello, $1"
}

log_result() {
    echo "$(date +%F) $1" >> ~/results.log
}

greet "Rushi"
greet "Yash"
log_result "Script completed"
```
```
Hello, Rushi
Hello, Yash
```

## Key Points
- Define BEFORE calling — bash reads top to bottom
- `$1` inside a function is the function's first argument
- Functions have their own `$1 $2` separate from the script's `$1 $2`
- No `function` keyword required — `name() {}` is enough
- Use `local varname` inside a function to keep variables local

## When I use this
Any task repeated more than once in a script — logging, checking
a service status, sending a notification.
