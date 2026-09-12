# actions/checkout — Get Your Code on the Runner

## What it does
Downloads your repository code onto the runner machine so
your workflow steps can actually see and work with your files.
Almost every workflow starts with this step.

## Syntax
```yaml
steps:
  - uses: actions/checkout@v4

  # checkout a specific branch
  - uses: actions/checkout@v4
    with:
      ref: main

  # checkout with full history
  - uses: actions/checkout@v4
    with:
      fetch-depth: 0
```

## Without checkout
```yaml
# this will NOT work — runner has no files
steps:
  - run: cat README.md
  # Error: README.md: No such file or directory
```

## With checkout
```yaml
# this works correctly
steps:
  - uses: actions/checkout@v4
  - run: cat README.md
  # output: contents of your README
```

## Key Points
- Without checkout, the runner is a blank machine with no repo files
- Almost every single workflow starts with `actions/checkout@v4`
- `@v4` pins the version — always pin, never use `@latest`
- `fetch-depth: 0` fetches the full git history (useful for tools that need it)
- Default checkout gets the branch that triggered the workflow

## Why @v4 and not @latest
```yaml
# GOOD — pinned version, reproducible
- uses: actions/checkout@v4

# BAD — could break if action releases a breaking change
- uses: actions/checkout@latest
```

## When I use this
Step one of every single workflow — without it nothing else works.
