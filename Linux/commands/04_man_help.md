# `man` & `--help` — Getting Help

## What it does
Gives you documentation and flag summaries for any command — right inside the terminal.

## Syntax
```bash
man <command>
<command> --help
whatis <command>
```

## Examples
```bash
# full manual for ls
$ man ls

# quick flag summary (faster to scan)
$ ls --help

# one-line description of what a command does
$ whatis ls
ls (1) - list directory contents
```

## Inside `man` — Navigation Keys

| Key | Action |
|-----|--------|
| `Space` | Scroll down one page |
| `b` | Scroll back one page |
| `/word` | Search for a term |
| `n` | Next search match |
| `q` | Quit and return to the prompt |

## Which to use when?

| Tool | Best for |
|------|----------|
| `man` | Full reference, when you need all details |
| `--help` | Quick flag lookup |
| `whatis` | Just need to know what something does |

## Key Points
- Stuck on a command? `man` it before searching the web
- `man` sections: `man(1)` = user commands, `man(5)` = file formats, `man(8)` = admin
- Not all tools have a man page, but most have `--help`
