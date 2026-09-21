# Freestyle Project — Creating Your First Jenkins Job

## What it is
The simplest type of Jenkins job. Configured by clicking through
the UI — no code required. Good for learning and simple tasks.
The starting point before moving to Pipeline jobs.

## Creating a Freestyle project
```
1. Dashboard → New Item
2. Enter a name: demo-pipeline
   (no spaces — use dashes or underscores)
3. Select "Freestyle project"
4. Click OK to open the configuration page
```

## Configuration sections
| Section | What you configure |
|---------|-------------------|
| General | Job description, parameters |
| Source Code Management | Which repo to clone |
| Build Triggers | When to run automatically |
| Build Environment | Tools, environment variables |
| Build Steps | The commands to execute |
| Post-build Actions | What to do after the build |

## Source Code Management — connect to Git
```
Section:          Source Code Management
Choose:           Git
Repository URL:   https://github.com/DevRushi-engg/Cloud-Devops.git
Credentials:      None needed for a public repo
Branch Specifier: */main
```

## Key Points
- Job names cannot contain spaces — use dashes or underscores
- For a public repo, URL and Branch Specifier are all you need
- Private repos need credentials added via Manage Jenkins → Credentials
- Each time the job runs, that is called a build, numbered #1, #2, #3
- A Freestyle job is roughly what a workflow file is in GitHub Actions

## Freestyle vs Pipeline
| Freestyle | Pipeline |
|-----------|---------|
| Click-through UI | Code in a Jenkinsfile |
| Settings live in Jenkins | Settings committed in your repo |
| Good for learning | Standard for real team projects |

## When I use this
Learning Jenkins, quick one-off automation tasks, and simple
jobs that do not need complex logic or version control.
