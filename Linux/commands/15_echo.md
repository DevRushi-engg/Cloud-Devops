# echo — Print Text and Variables

## What it does
Prints text or the value of a variable to the terminal.

## Syntax
```bash
echo "Hello, World"
echo $HOME
echo $USER
echo $PATH
```

## My Terminal Output
```bash
rushi@rushi:~$ echo "Hello, deboistech"
Hello, deboistech

rushi@rushi:~$ echo $HOME
/home/rushi

rushi@rushi:~$ echo $USER
rushi
```

## Key Points
- `$HOME`, `$USER`, `$PATH` are built-in environment variables
- `echo` is the foundation of shell scripting
- Use `>>` to append output to a file: `echo "text" >> file.txt`

## When I use this
Debugging variable values in scripts and writing quick text into files.
