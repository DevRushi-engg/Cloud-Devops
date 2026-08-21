# for & while — Loops in Shell Scripts

## What it does
Repeats a block of commands for each item in a list (for)
or as long as a condition is true (while).

## for loop syntax
```bash
for i in 1 2 3; do
    echo "Number $i"
done

# loop over files
for f in *.log; do
    echo "Processing $f"
done

# loop over a range
for i in {1..5}; do
    echo "Line $i"
done
```

## while loop syntax
```bash
count=1
while [ $count -le 3 ]; do
    echo "count $count"
    count=$((count + 1))
done
```

## My Terminal Output
```bash
rushi@rushi:~$ for i in 1 2 3; do echo "Number $i"; done
Number 1
Number 2
Number 3

rushi@rushi:~$ count=1
rushi@rushi:~$ while [ $count -le 3 ]; do
> echo "count $count"
> count=$((count+1))
> done
count 1
count 2
count 3
```

## Arithmetic in scripts
```bash
count=$((count + 1))    # addition
result=$((5 * 3))       # multiplication
```

## Key Points
- `for` is best when you know the list in advance
- `while` is best when you keep going until something changes
- Always update the condition variable in a while loop — or it loops forever
- `$((...))` is how you do arithmetic in bash
- Loop over files with `for f in *.log` — very useful in DevOps scripts

## When I use this
Processing multiple log files, retrying a command until it succeeds,
counting through a range of numbers.
