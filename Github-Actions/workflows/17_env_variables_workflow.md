# env: — Environment Variables in Workflows

## What it does
Defines environment variables available to commands in your workflow.
Can be set at workflow level, job level, or step level.
Inner values override outer ones.

## Syntax
```yaml
# workflow level — available to ALL jobs and steps
env:
  APP_NAME: cloud-devops
  VERSION: "1.0.0"

jobs:
  build:
    runs-on: ubuntu-latest

    # job level — available to ALL steps in this job
    env:
      NODE_ENV: production

    steps:
      - uses: actions/checkout@v4

      # step level — available to THIS step only
      - name: Show all variables
        env:
          GREETING: hello
        run: |
          echo "$APP_NAME"
          echo "$NODE_ENV"
          echo "$GREETING"
          echo "$VERSION"
```

## Scope hierarchy
```
workflow env:  → available everywhere
  job env:     → overrides workflow level for this job
    step env:  → overrides job level for this step
```

## Built-in GitHub variables
```yaml
steps:
  - run: echo "Repo:   ${{ github.repository }}"
  - run: echo "Actor:  ${{ github.actor }}"
  - run: echo "Branch: ${{ github.ref_name }}"
  - run: echo "SHA:    ${{ github.sha }}"
  - run: echo "Event:  ${{ github.event_name }}"
```

## Key Points
- `$VARIABLE_NAME` in `run:` commands — same as regular Linux shell
- `${{ github.* }}` uses GitHub's expression syntax — different from env vars
- Inner scope overrides outer — step env beats job env beats workflow env
- Do NOT put secrets in `env:` — use `${{ secrets.NAME }}` instead
- Use ALL_CAPS by convention for environment variable names

## When I use this
Sharing configuration values across jobs, setting the environment
name for deployments, passing version numbers to build commands.
