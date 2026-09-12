# Workflow File Structure — name, on, jobs

## What it is
Every workflow file answers three questions:
- `name:` what is this workflow called
- `on:` when does it run
- `jobs:` what does it do

## Where workflows live
```bash
# must be exactly this path
.github/workflows/ci.yml

# create the folder
mkdir -p .github/workflows

# create the workflow file
nano .github/workflows/ci.yml
```

## Complete minimal workflow
```yaml
name: CI

on: push

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: echo "Build complete"
```

## The three required sections
```yaml
# SECTION 1 — name (shows in Actions tab)
name: My Pipeline

# SECTION 2 — on (when it runs)
on: push

# SECTION 3 — jobs (what it does)
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo "hi"
```

## Key Points
- The path must be exactly `.github/workflows/` or GitHub ignores the file
- `workflows` is plural — `.github/workflow/` without the s will not work
- You can have many `.yml` files in the folder — each is an independent workflow
- The `name:` value is what appears in the GitHub Actions tab
- Commit the file to trigger it for the first time

## When I use this
Creating every new workflow — this three-section structure
is the skeleton every workflow file starts with.
