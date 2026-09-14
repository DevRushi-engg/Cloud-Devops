# if: — Skip Steps or Jobs Conditionally

## What it does
Evaluates an expression before running a step or job.
If the expression is false, the step or job is skipped.

## Syntax
```yaml
steps:
  - uses: actions/checkout@v4

  # only runs on the main branch
  - name: Deploy to production
    if: github.ref == 'refs/heads/main'
    run: echo "Deploying to production"

  # only runs on pull requests
  - name: PR comment
    if: github.event_name == 'pull_request'
    run: echo "This is a PR run"

  # only runs if a previous step failed
  - name: Notify on failure
    if: failure()
    run: echo "Something went wrong"

  # only runs if everything succeeded
  - name: Notify on success
    if: success()
    run: echo "All good"
```

## Common if: expressions
| Expression | When it is true |
|-----------|----------------|
| `github.ref == 'refs/heads/main'` | Push to main branch |
| `github.event_name == 'push'` | Triggered by a push |
| `github.event_name == 'pull_request'` | Triggered by a PR |
| `github.actor == 'DevRushi-engg'` | Specific user triggered |
| `success()` | All previous steps passed |
| `failure()` | Any previous step failed |
| `always()` | Runs regardless of previous results |

## Conditional jobs
```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: npm test

  deploy:
    needs: test
    if: github.ref == 'refs/heads/main'   # deploy only from main
    runs-on: ubuntu-latest
    steps:
      - run: echo "Deploying"
```

## Key Points
- `if:` uses GitHub's expression syntax — note the `${{ }}` is optional here
- `failure()` is useful for cleanup steps that must run even when things break
- `always()` runs unconditionally — good for notification steps
- Combine with `needs:` for deploy-only-on-main-after-tests patterns
- Skipped steps show as grey in the Actions UI — not a failure

## When I use this
Running deploys only from the main branch, sending notifications
only on failure, running cleanup steps regardless of outcome.
