# jobs: and runs-on: — Defining Jobs and Machines

## What it does
`jobs:` holds one or more named jobs.
`runs-on:` tells GitHub which machine to use for that job.

## Syntax
```yaml
jobs:
  build:                        # job name — you choose this
    runs-on: ubuntu-latest      # machine type

  test:
    runs-on: ubuntu-latest

  deploy:
    runs-on: ubuntu-latest
    needs: test                 # only runs if test passes
```

## Available runners
| Value | Machine |
|-------|---------|
| `ubuntu-latest` | Ubuntu Linux — use this most of the time |
| `windows-latest` | Windows Server |
| `macos-latest` | macOS |

## Multiple jobs
```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: echo "Building"

  test:
    runs-on: ubuntu-latest
    needs: build                # waits for build to finish
    steps:
      - run: echo "Testing"
```

## Key Points
- `ubuntu-latest` is the right choice for almost everything
- Each job gets a completely fresh machine — no files carry between jobs
- Jobs run in parallel by default — use `needs:` to sequence them
- The job name (`build`, `test`) is what appears in the workflow diagram
- A fresh machine spins up, runs your steps, reports result, then disappears
- GitHub hosts these machines — you pay nothing for public repos

## When I use this
Every workflow has at least one job. I add more jobs when I want
to separate concerns — build in one job, test in another,
deploy in a third.
