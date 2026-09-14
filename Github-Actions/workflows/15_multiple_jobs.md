# Multiple Jobs — Parallel and Sequential

## What it does
A workflow can have multiple jobs running on separate machines.
By default jobs run in parallel — making the pipeline faster.
Use `needs:` to make jobs run in sequence.

## Parallel jobs (default)
```yaml
name: CI
on: push

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: echo "Lint running"

  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: echo "Tests running"
```
Both jobs start at the same time on separate machines.
Their logs appear side by side in the Actions tab.

## Sequential jobs with needs:
```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: echo "Running tests"

  build:
    needs: test              # waits for test to pass
    runs-on: ubuntu-latest
    steps:
      - run: echo "Building"

  deploy:
    needs: build             # waits for build to pass
    runs-on: ubuntu-latest
    steps:
      - run: echo "Deploying"
```

## The shape
```
test ──→ build ──→ deploy
         needs:test  needs:build
```
A red X anywhere stops everything after it.
Never deploy a build that never tested.

## Key Points
- Jobs run in parallel by default — faster pipelines
- Each job gets a completely fresh machine
- `needs: job-name` makes a job wait and only run if the previous passed
- `needs:` takes a list too: `needs: [test, lint]`
- A failed job cancels all jobs that `needs:` it

## When I use this
Separating concerns — lint in one job, test in another,
deploy only after both pass.
