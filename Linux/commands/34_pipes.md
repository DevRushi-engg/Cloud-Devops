# Pipes — | and tee

## What it does
`|` connects one command's output directly into the next command's input.
`tee` splits output to both the screen and a file at the same time.

## Syntax
```bash
cat app.log | grep ERROR | wc -l          # pipe chain
grep ERROR app.log | tee errors.txt       # save AND see
grep ERROR app.log | tee -a errors.txt    # append version
```

## My Terminal Output
```bash
rushi@rushi:~$ cat server.log | grep ERROR | wc -l
3

rushi@rushi:~$ grep ERROR server.log | tee error_summary.txt
ERROR disk full
ERROR timeout
ERROR disk full
# output printed to screen AND saved to file
```

## Key Points
- Read a pipeline left to right — each `|` hands the result to the next tool
- No temporary files needed — data flows through memory
- Chain as many stages as you like
- `tee` is named after a T-shaped pipe fitting — splits in two directions
- `tee -a` appends instead of overwriting

## Classic pipeline pattern
```bash
grep ERROR app.log | sort | uniq -c | sort -rn | head -5
# filter → sort → count → rank → top 5
```

## When I use this
All the time — filtering logs, counting results, building multi-step
data processing without writing temp files.
