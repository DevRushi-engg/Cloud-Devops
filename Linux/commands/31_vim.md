# vim — Powerful Terminal Editor

## What it does
A powerful editor available on virtually every Linux machine by default.
Works with modes — this is what confuses beginners at first.

## Syntax
```bash
vim notes.txt        # open or create a file
```

## The Two Main Modes
| Mode | What it does |
|------|-------------|
| Normal mode | Keys are commands — move, delete, copy |
| Insert mode | Keys type text like a normal editor |

You always start in **Normal mode**.

## Getting In and Out of Insert Mode
```bash
i        # insert before cursor
a        # insert after cursor
o        # open new line below and insert
Esc      # leave insert mode, back to normal
```

## Saving and Quitting (from Normal mode — press Esc first)
```bash
:w       # save (write)
:wq      # save and quit
:q!      # quit WITHOUT saving — the escape hatch
```

## My Terminal Output
```bash
rushi@rushi:~$ vim notes.txt
# press i to start typing
Hello from vim!
# press Esc then :wq to save and exit
```

## Essential Commands
| Command | What it does |
|---------|-------------|
| `i / a / o` | Insert before / after / new line |
| `Esc` | Return to Normal mode |
| `dd` | Delete current line |
| `yy` | Copy current line |
| `p` | Paste |
| `/word` | Search for a word |
| `:wq` | Save and quit |
| `:q!` | Quit without saving |

## Key Points
- Press `i` to type, press `Esc` to stop typing — that is 90% of vim
- Stuck? Press `Esc` then type `:q!` to get out
- `:wq` is your everyday save and exit
- vim is on every Linux machine — even minimal server installs

## When I use this
When nano is not available, or when editing files that need
vim-specific features like macros and column editing.
