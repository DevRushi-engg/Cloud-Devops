# Environment Variables in GitHub Actions

## What it is
Variables available during a workflow run.
GitHub provides built-in variables and you can define your own.

## Built-in GitHub variables
```yaml
steps:
  - run: echo "Repo: $GITHUB_REPOSITORY"
  - run: echo "Branch: $GITHUB_REF_NAME"
  - run: echo "Commit: $GITHUB_SHA"
  - run: echo "Actor: $GITHUB_ACTOR"
  - run: echo "Workspace: $GITHUB_WORKSPACE"
```

## Define your own variables
```yaml
# workflow level — available to all jobs
env:
  NODE_ENV: production
  APP_NAME: cloud-devops

jobs:
  build:
    runs-on: ubuntu-latest
    # job level — available to all steps in this job
    env:
      BUILD_VERSION: "1.0.0"
    steps:
      # step level — available to this step only
      - name: Print vars
        env:
          STEP_VAR: "hello"
        run: |
          echo "$NODE_ENV"
          echo "$BUILD_VERSION"
          echo "$STEP_VAR"
```

## Common built-in variables
| Variable | What it contains |
|----------|----------------|
| `GITHUB_REPOSITORY` | `owner/repo-name` |
| `GITHUB_SHA` | Full commit hash |
| `GITHUB_REF_NAME` | Branch or tag name |
| `GITHUB_ACTOR` | Username who triggered the run |
| `GITHUB_WORKSPACE` | Path to checked out code |
| `GITHUB_EVENT_NAME` | Event that triggered: push, pull_request |

## Key Points
- Built-in variables start with `GITHUB_` — no definition needed
- Custom variables are defined under `env:` at workflow, job, or step level
- More specific levels override less specific ones
- Use `$VARIABLE_NAME` in `run:` commands — same as regular Linux shell
- Secrets are different from env vars — never put secrets in `env:`

## When I use this
Adding context to log output, controlling build behavior by
environment, making workflows reusable across repos.
