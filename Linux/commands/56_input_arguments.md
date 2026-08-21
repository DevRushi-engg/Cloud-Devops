# Input & Arguments — Getting Data Into a Script

## What it does
Two ways to pass data into a script:
- `read` — interactive prompt during runtime
- `$1 $2` — arguments passed when calling the script

## Syntax
```bash
# interactive input
read -p "Enter your name: " name
echo "Hello, $name"

# script arguments
echo "First arg: $1"
echo "Second arg: $2"
echo "All args: $@"
echo "Count: $#"
```

## My Terminal Output
```bash
# interactive
rushi@rushi:~$ bash greet.sh
Enter your name: Rushi
Hello, Rushi

# arguments
rushi@rushi:~$ bash greet.sh Rushi DevOps
First arg: Rushi
Second arg: DevOps
All args: Rushi DevOps
Count: 2
```

## read flags
| Flag | What it does |
|------|-------------|
| `-p` | Show a prompt before waiting for input |
| `-s` | Silent mode — hides input (good for passwords) |

## Key Points
- `read -p "prompt: " varname` in one line is the cleanest form
- `$1` is the first argument, `$2` the second, and so on
- `$@` gives you all arguments — useful in loops
- `$#` tells you how many arguments were passed
- Use `$#` to validate that the right number of arguments were given

## When I use this
Making scripts flexible — passing a filename, username, or
environment name at runtime instead of hardcoding it.
