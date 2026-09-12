# YAML Basics — Just Enough to Write Workflows

## What it is
YAML is the format used to write GitHub Actions workflow files.
It uses indentation to show structure — no brackets or commas.

## Core Rules
```yaml
# key: value pairs
name: My Workflow

# nested structure with indentation (2 spaces per level)
jobs:
  build:
    runs-on: ubuntu-latest

# list items start with a dash
steps:
  - run: echo "step one"
  - run: echo "step two"

# inline list
on: [push, pull_request]
```

## Indentation rules
```yaml
# CORRECT — 2 spaces
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: echo "hi"

# WRONG — tabs cause errors
jobs:
	build:         # ← TAB — this breaks everything
```

## Reading a YAML workflow
```yaml
name: Say Hello       # string value
on: push              # trigger event
jobs:                 # map of jobs
  greet:              # job name (you choose this)
    runs-on: ubuntu-latest   # machine type
    steps:            # list of steps
      - run: echo "Hello, Actions!"   # shell command
```

## Key Points
- Indentation MUST be spaces — tabs are forbidden in YAML
- Two spaces per level is the standard for GitHub Actions
- A colon `:` separates key from value — always followed by a space
- A dash `-` starts a list item
- One wrong space breaks the whole file — YAML is strict
- `#` starts a comment — ignored by GitHub

## Common YAML gotchas
| Mistake | Fix |
|---------|-----|
| Tab instead of space | Use spaces only — configure editor to expand tabs |
| Missing space after `:` | `name: value` not `name:value` |
| Wrong indentation level | Count spaces carefully |
| Quotes missing around special chars | Wrap values with `:` or `#` in quotes |

## When I use this
Every time I write a workflow file — YAML syntax is the
first thing to get right before any logic works.
