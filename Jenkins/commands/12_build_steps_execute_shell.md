# Build Steps — Execute Shell

## What it is
The actual commands that run during a build.
In Freestyle jobs, the most common build step is "Execute shell" —
which runs Linux commands on the build machine.

## Adding a build step
```
In job configuration → Build Steps section
→ Click "Add build step"
→ Choose "Execute shell"
→ Type your commands in the text box
→ Click Save
```

## A safe first build step
```bash
echo "Building the project"
pwd
ls -la
date
```
This always succeeds since it needs no project-specific tools.

## A more realistic build step
```bash
echo "=== Starting build ==="
echo "Branch: $GIT_BRANCH"
echo "Commit: $GIT_COMMIT"
echo "Build number: $BUILD_NUMBER"

# your actual commands here
# npm install
# npm test
# npm run build

echo "=== Build complete ==="
```

## Jenkins built-in environment variables in shell steps
| Variable | What it contains |
|----------|----------------|
| `$BUILD_NUMBER` | The build number: 1, 2, 3 |
| `$JOB_NAME` | The name of the job |
| `$WORKSPACE` | Path to the checked-out code |
| `$GIT_BRANCH` | The branch that triggered the build |
| `$GIT_COMMIT` | The full commit hash |
| `$BUILD_URL` | URL to this specific build |

## Key Points
- Commands run exactly as they would in a Linux terminal
- If any command exits with a non-zero code, the build fails
- Multiple commands can be in one Execute Shell box, one per line
- Add multiple Execute Shell steps to separate concerns
- This is Jenkins' equivalent of a `run:` line in GitHub Actions
- The commands run in `$WORKSPACE` — your checked-out repo directory

## When I use this
Every Freestyle job needs at least one build step — this is where
the actual work of the build happens.
