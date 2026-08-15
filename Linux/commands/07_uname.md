# uname — System Information

## What it does
Prints information about the system and kernel.

## Syntax
```bash
uname -a      # full system info in one line
uname -r      # just the kernel version
```

## My Terminal Output
```bash
rushi@rushi:~$ uname -a
Linux rushi 6.5.0-45-generic x86_64 GNU/Linux

rushi@rushi:~$ uname -r
6.5.0-45-generic
```

## Flags
| Flag | What it does |
|------|-------------|
| `-a` | All info: kernel name, hostname, version, architecture |
| `-r` | Kernel release version only |

## When I use this
When a tool or driver requires a specific kernel version to confirm compatibility.
