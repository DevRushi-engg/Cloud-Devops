# The Four Building Blocks — Workflow, Job, Step, Action

## What they are
Every GitHub Actions pipeline is built from four nested pieces.
Understanding how they nest explains every workflow you will read.

## The Four Pieces
| Piece | What it is |
|-------|-----------|
| Workflow | The whole automated process — one `.yml` file |
| Job | A group of steps that run on one machine |
| Step | A single task — run a command or use an action |
| Action | A reusable prebuilt unit you plug into a step |

## How they nest
```
WORKFLOW  (ci.yml)
└── JOB: build-and-test
    ├── STEP: check out the code     → uses: actions/checkout@v4
    ├── STEP: install dependencies   → run: npm install
    └── STEP: run the tests          → run: npm test
```

## Key Points
- Workflow contains jobs
- Jobs contain steps
- Steps either `run` a shell command or `uses` a prebuilt action
- One workflow file can have multiple jobs
- Jobs run in parallel by default — use `needs:` to make them sequential
- Each job gets a fresh machine — no state carries between jobs

## Simple example
```yaml
name: CI
on: push
jobs:
  test:                          # JOB name
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4  # STEP using an ACTION
      - run: echo "Hello"          # STEP running a COMMAND
```

## When I use this
This mental model is active every time I write or read a
workflow file — knowing which layer I am in tells me the
correct syntax to use.
