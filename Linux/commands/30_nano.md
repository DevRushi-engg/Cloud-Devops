# nano — Beginner Friendly Terminal Editor

## What it does
Opens a simple text editor directly in the terminal with a help
menu at the bottom. No modes — you type and it types.

## Syntax
```bash
nano notes.txt        # open or create a file
```

## My Terminal Output
```
  GNU nano 6.2               notes.txt

Hello from nano!

^G Help    ^O Write Out    ^X Exit    ^K Cut    ^U Paste
```

## Keyboard Shortcuts
| Shortcut | What it does |
|----------|-------------|
| `Ctrl+O` | Save the file (Write Out) |
| `Ctrl+X` | Exit the editor |
| `Ctrl+K` | Cut the current line |
| `Ctrl+U` | Paste the cut line |
| `Ctrl+W` | Search within the file |

## Key Points
- `^` in the menu means the `Ctrl` key
- Just start typing — no mode switching needed
- `Ctrl+O` then `Enter` to confirm filename when saving
- If you only want to exit without saving: `Ctrl+X` then `N`

## When I use this
Quick edits to config files on a server when I just need to change
one line fast.
