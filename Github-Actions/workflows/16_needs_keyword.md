# needs: — Job Dependencies and Ordering

## What it does
Makes a job wait for one or more other jobs to complete
successfully before it starts.
If the dependency fails, the dependent job is skipped.

## Syntax
```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm test

  deploy:
    needs: test                    # single dependency
    runs-on: ubuntu-latest
    steps:
      - run: echo "Deploying"

  notify:
    needs: [test, deploy]          # multiple dependencies
    runs-on: ubuntu-latest
    steps:
      - run: echo "All done"
```

## My Terminal Output (Actions tab)
```
✅ test      (passes)
    ↓
✅ deploy    (runs because test passed)
    ↓
✅ notify    (runs because both passed)

❌ test      (fails)
    ↓
⏭️ deploy    (skipped — test failed)
⏭️ notify    (skipped — dependency failed)
```

## Key Points
- The job name in `needs:` must match exactly — case sensitive
- Use a list `needs: [job1, job2]` to wait for multiple jobs
- A skipped job shows as grey in the Actions UI — not a failure
- This is how you build test → build → deploy pipelines safely
- `needs:` creates a directed acyclic graph (DAG) of jobs

## When I use this
Any time the output of one job is required for the next —
especially deploy jobs that must only run after tests pass.
