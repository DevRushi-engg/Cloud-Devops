# workflow_dispatch — Manual Run Button

## What it does
Adds a "Run workflow" button in the GitHub Actions tab so you
can trigger a workflow manually without pushing code.
Optionally accepts inputs from the person triggering it.

## Syntax
```yaml
# basic — just adds a run button
on: workflow_dispatch

# with required inputs
on:
  workflow_dispatch:
    inputs:
      environment:
        description: "Which environment to deploy to"
        required: true
        default: "staging"
        type: choice
        options:
          - staging
          - production
      debug:
        description: "Enable debug logging"
        required: false
        type: boolean
        default: false
```

## Using inputs in steps
```yaml
steps:
  - run: echo "Deploying to ${{ github.event.inputs.environment }}"
  - run: echo "Debug mode: ${{ github.event.inputs.debug }}"
```

## My example
```yaml
name: Manual Health Check

on: workflow_dispatch

jobs:
  check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: echo "Manual health check triggered"
      - run: echo "Triggered by ${{ github.actor }}"
```

## Key Points
- Button appears in Actions tab → select workflow → Run workflow
- Without inputs it is just a trigger button — simplest form
- With inputs you can make a flexible deployment workflow
- `github.actor` gives you who clicked the button
- Can be combined with other triggers: `on: [push, workflow_dispatch]`

## When I use this
Deployment workflows where you want manual control over when
something goes to production, and for ad-hoc maintenance tasks.

