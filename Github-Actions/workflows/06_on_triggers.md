# on: — Triggers, When Workflows Run

## What it does
The `on:` keyword defines which GitHub events cause the
workflow to run.

## Common Triggers
```yaml
# run on every push to any branch
on: push

# run when a pull request is opened or updated
on: pull_request

# run on both
on: [push, pull_request]

# run on a schedule (cron syntax)
on:
  schedule:
    - cron: "0 2 * * *"    # every day at 2am

# manual run button in GitHub Actions tab
on: workflow_dispatch
```

## Narrow to specific branches
```yaml
on:
  push:
    branches:
      - main
      - develop

  pull_request:
    branches:
      - main
```

## Narrow to specific file paths
```yaml
on:
  push:
    paths:
      - "src/**"
      - "*.py"
```

## My Terminal Output
```bash
# after pushing a file with on: push trigger
rushi@rushi:~/Cloud-Devops$ git push
# GitHub detects the push and starts the workflow
# visible in the Actions tab within seconds
```

## Key Points
- `push` and `pull_request` are what you will use 90% of the time
- `workflow_dispatch` adds a manual Run button — useful for deployments
- `schedule` uses standard cron syntax — same as Linux cron
- Narrowing to `branches: [main]` prevents noise from every feature branch
- Multiple triggers can be combined with a list `[push, pull_request]`

## When I use this
Every workflow — choosing the right trigger is the first
decision after creating the file.

