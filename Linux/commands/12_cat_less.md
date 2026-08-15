# cat & less — Read File Contents

## What it does
`cat` dumps the whole file to terminal. `less` opens it page by page.

## Syntax
```bash
cat app.log                    # print whole file
cat file1 file2 > combined.log # combine two files into one
less app.log                   # page through large file
```

## My Terminal Output
```bash
rushi@rushi:~/practice$ cat logs/app.log
line1
line2
line3
```

## Key Points
- `cat` is best for short files — long files scroll past instantly
- `less` controls: `Space` = next page, `b` = back, `/word` = search, `q` = quit
- Prefer `less` over `more` — less lets you scroll both directions
- `cat file1 file2 > combined` merges files

## When I use this
`cat` for quick checks on small files. `less` for log files and large configs.
