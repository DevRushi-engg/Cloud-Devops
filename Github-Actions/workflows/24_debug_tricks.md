# Debugging Workflows — Tricks That Save Hours

## What it does
Techniques for finding and fixing failures in GitHub Actions
without guessing.

## Reading a failed run
```
1. Actions tab → click the failed run (red X)
2. Click the failed job name
3. Click the failed step name
4. Scroll to the red lines — the error is there
5. Check "Annotations" at the top for a summary
```

## Debug steps to add temporarily
```yaml
steps:
  - uses: actions/checkout@v4

  - name: Debug environment
    run: |
      pwd
      ls -la
      node --version || true
      python3 --version || true
      env | sort | head -30
```

## || true — prevent diagnostic failures
```yaml
# without || true — workflow fails if node is not installed
- run: node --version

# with || true — shows the version or "not found" and continues
- run: node --version || true
```

## Check if a secret is set without printing it
```yaml
- name: Verify secret exists
  env:
    TOKEN: ${{ secrets.MY_TOKEN }}
  run: |
    if [ -z "$TOKEN" ]; then
      echo "ERROR: MY_TOKEN secret is not set"
      exit 1
    fi
    echo "MY_TOKEN is set (${#TOKEN} characters)"
```

## Common failures and fixes
| Error | Likely cause | Fix |
|-------|-------------|-----|
| `No such file or directory` | Missing checkout | Add `actions/checkout@v4` as first step |
| `npm: command not found` | Missing setup step | Add `actions/setup-node@v4` |
| `Process exit code 1` | Test or command failed | Read step output for details |
| `yaml: found character that cannot start any token` | Tab in YAML | Replace tabs with spaces |
| `Unable to resolve action` | Wrong version format | Use `@v4` not `@4` |
| Workflow never triggers | Wrong folder name | Must be `.github/workflows/` plural |

## Enable debug logging
```
GitHub → Actions tab → Re-run jobs → Enable debug logging
```
This adds very verbose output to every step — useful for hard to find issues.

## Key Points
- Always read the log from top to bottom — the root cause is usually early
- `|| true` is safe for diagnostic commands that might not exist
- Fix code or YAML → push → new run starts automatically
- A failing pipeline is not a disaster — it caught something before users did
- Adding `echo` statements for debugging is always the right first move

## When I use this
Every time a workflow fails — systematic log reading beats
random guessing every time.
