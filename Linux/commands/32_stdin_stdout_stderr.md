# stdin, stdout, stderr — The Three I/O Streams

## What it is
Every Linux command has three channels for data flowing in and out.

## The Three Streams
| Stream | Number | What it carries |
|--------|--------|----------------|
| `stdin` | 0 | Input going INTO the command |
| `stdout` | 1 | Normal output coming OUT |
| `stderr` | 2 | Error messages coming OUT |

## Why they are separate
Normal output and errors travel on different channels.
This is what makes redirection and pipes clean and reliable —
you can capture just errors, or throw them away, without touching
normal output.

## My Terminal Output
```bash
# stdout — normal output
rushi@rushi:~$ ls /home
rushi

# stderr — error message on a different channel
rushi@rushi:~$ ls /nope
ls: cannot access '/nope': No such file or directory
```

## Key Points
- By default both stdout and stderr print to your terminal
- They only separate when you redirect them
- `0`, `1`, `2` are the file descriptor numbers used in redirection
- Understanding this is the foundation for all redirection commands

## When I use this
Every time I redirect output or errors — this is the mental model
behind `>`, `2>`, and `2>&1`.

