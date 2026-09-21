# Console Output — Reading Build Logs

## What it is
The live log of everything that happened during a build.
The first place to look when a build fails.

## Accessing console output
```
Dashboard → click job name → click build number (#1, #2...)
→ click "Console Output" in the left sidebar
```
Or directly: `http://localhost:8080/job/my-job/1/console`

## What console output looks like
```
Started by user admin
Running as SYSTEM
Building in workspace /var/lib/jenkins/workspace/demo-pipeline
The recommended git tool is: NONE
Cloning repository https://github.com/DevRushi-engg/Cloud-Devops.git
Checking out Revision abc1234 (refs/remotes/origin/main)

[demo-pipeline] $ /bin/sh -xe /tmp/jenkins123.sh
+ echo Building the project
Building the project
+ pwd
/var/lib/jenkins/workspace/demo-pipeline
+ ls -la
total 24
drwxr-xr-x 3 jenkins jenkins 4096 Aug 11 README.md

Finished: SUCCESS
```

## Reading the last line
| Last line | Meaning |
|-----------|---------|
| `Finished: SUCCESS` | All steps passed |
| `Finished: FAILURE` | A step returned a non-zero exit code |
| `Finished: UNSTABLE` | Build ran but tests failed |
| `Finished: ABORTED` | Manually stopped before finishing |

## Common errors in console output
| Error | Cause |
|-------|-------|
| `ERROR: repository not found` | Wrong repo URL or private repo needs credentials |
| `command not found` | Tool not installed on the build machine |
| `Permission denied` | Wrong file permissions or missing credentials |
| `fatal: could not read Username` | Private repo needs credentials configured |

## Key Points
- Always check the very last line first — it tells you the overall result
- Work upward from the last red line to find the root cause
- `+ command` lines show the actual commands that ran
- A spinning icon on the build number means it is still running
- Console Output updates live while the build is running

## When I use this
Every time a build fails — console output is always the first
place to look. The answer is always in the log.
