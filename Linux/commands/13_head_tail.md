# head & tail — Peek at Files

## What it does
`head` shows the beginning of a file. `tail` shows the end.

## Syntax
```bash
head -n 5 app.log      # first 5 lines
tail -n 5 app.log      # last 5 lines
tail -f app.log        # follow live — streams new lines as written
```

## My Terminal Output
```bash
rushi@rushi:~/practice$ head -n 2 logs/app.log
line1
line2

rushi@rushi:~/practice$ tail -n 2 logs/app.log
line2
line3
```

## Key Points
- Default is 10 lines if you don't specify `-n`
- `tail -f` is extremely useful for watching live application logs
- Press `Ctrl+C` to stop `tail -f`

## When I use this
`tail -f` constantly when monitoring running services and checking recent errors.
