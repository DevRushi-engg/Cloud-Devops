# Linux Permissions Model — rwx Explained

## What it does
Every file in Linux has a permission string that controls who can
read, write, or execute it.

## Reading the Permission String
```bash
$ ls -l
-rwxr-xr-- 1 rushi devs 512 Aug 11 app.sh
```

Breaking it down:
d rwx r-x r--
│  │  │    │
│  │  │    └── others (everyone else)
│  │  └────── group
│  └────────── owner
└───────────── type: - file, d directory, l symlink


## What r, w, x Mean
| Letter | On a file | On a folder |
|--------|-----------|-------------|
| `r` read | View the contents | List what is inside |
| `w` write | Change the contents | Add or remove items |
| `x` execute | Run it as a program | Enter it with cd |

## Key Points
- Permissions come in 3 groups of 3: owner, group, others
- `x` on a folder means permission to enter it — not to run it
- `a` is shorthand for all three: owner + group + others
- First character tells the type: `-` file, `d` directory, `l` symlink

## Common Permission Patterns
| String | Octal | Meaning |
|--------|-------|---------|
| `rwxr-xr-x` | 755 | Script or folder — owner full, rest read+enter |
| `rw-r--r--` | 644 | Regular file — owner edits, rest read only |
| `rw-------` | 600 | Private file — owner only |
| `rwx------` | 700 | Private folder or script — owner only |

## When I use this
Every time I need to understand why something says "Permission denied".
