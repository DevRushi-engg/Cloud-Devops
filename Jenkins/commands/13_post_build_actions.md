# Post-Build Actions — After the Build Finishes

## What it is
Steps that run after the main build completes — whether it
passed or failed. Used for archiving output, sending notifications,
and triggering downstream jobs.

## Adding a post-build action
```
In job configuration → Post-build Actions section
→ Click "Add post-build action"
→ Choose the action type
→ Configure it
→ Click Save
```

## Common post-build actions
| Action | What it does |
|--------|-------------|
| Archive the artifacts | Save build output files for download |
| Publish JUnit test results | Show test report in the build summary |
| Email notification | Send email if build fails |
| Trigger parameterized build | Start another job when this one finishes |
| Slack Notifications (plugin) | Send message to Slack channel |

## Archiving artifacts
```
Post-build Actions → Archive the artifacts
Files to archive: dist/**,*.log
```
After the build, click the build number → Artifacts to download them.

## JUnit test results
```
Post-build Actions → Publish JUnit test results
Test report XMLs: **/test-results/*.xml
```
Jenkins shows pass/fail trends across builds.

## Email notification
```
Post-build Actions → Email Notification
Recipients: your@email.com
Tick: Send e-mail for every unstable build
```

## Key Points
- Post-build actions run even if the build failed — useful for cleanup
- Archived artifacts survive job deletion by default
- This is Jenkins' version of GitHub Actions' `upload-artifact` and `needs:`
- Email notifications require the SMTP settings in Manage Jenkins → System
- Triggering downstream jobs is how you chain Jenkins pipelines

## When I use this
Every real job should archive artifacts and send failure
notifications — these are the minimum post-build actions for
any job that matters.
