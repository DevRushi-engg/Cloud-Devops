# Debugging Failed Workflows

## What it is
When a workflow shows a red X, reading the logs tells you
exactly what went wrong and where.

## Finding the error
```
1. Go to GitHub → Actions tab
2. Click the failed run (red X)
3. Click the failed job
4. Click the failed step
5. Read the last few red lines — the error is there
6. Fix your code or YAML and push again
```

## Common errors and fixes
| Error | Cause | Fix |
|-------|-------|-----|
| `No such file or directory` | Missing `actions/checkout` | Add checkout as first step |
| `yaml: line X: found a tab` | Tab in YAML file | Replace all tabs with spaces |
| `not found in .github/workflows` | Wrong folder name | Check `workflows` is plural |
| `Process completed with exit code 1` | Command failed | Read the step output for details |
| `Error: Cannot find module` | Missing install step | Add `run: npm install` before test |

## Adding debug output
```yaml
steps:
  - uses: actions/checkout@v4

  - name: Debug environment
    run: |
      echo "Branch: $GITHUB_REF_NAME"
      echo "Commit: $GITHUB_SHA"
      echo "Runner OS: $RUNNER_OS"
      pwd
      ls -la
```

## Re-running a failed workflow
```
Actions tab → failed run → Re-run jobs → Re-run failed jobs
```

## Key Points
- A failing workflow is not a disaster — it caught a problem
- Fix the code or YAML, push again, new run starts automatically
- The error is almost always in the last few red lines of the log
- Add `echo` statements for debugging — they appear in the step log
- Check YAML indentation first — it is the most common cause of failures

## When I use this
Every time a workflow fails — reading logs is the first step,
guessing is the last resort.
