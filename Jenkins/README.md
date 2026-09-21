# Jenkins

This folder contains my learning notes from the Jenkins module
of the deboistech Multi-Cloud Engineering cohort.

## What is Jenkins?
Jenkins is an open source automation server you install and run
on your own infrastructure. It watches your repository and runs
CI/CD pipelines automatically when code changes.
Unlike GitHub Actions which runs on GitHub's servers, Jenkins
runs on a server you fully control.

## What is in this folder?
- `commands/` — one file per Jenkins concept with steps and notes
- `sessions/` — session summaries covering what was taught each day

## Module Structure
| Day | Topic |
|-----|-------|
| Day 1 | Jenkins install, Freestyle jobs, dashboard, plugins |

## Key Concepts
- **Controller** — the main Jenkins server, schedules jobs
- **Agent** — separate machine that actually runs builds
- **Job** — one thing Jenkins knows how to build
- **Build** — one run of a job, numbered #1 #2 #3
- **Executor** — a slot that runs exactly one build at a time
- **Plugin** — adds capabilities Jenkins does not have by default

## Jenkins runs on port 8080
```
http://localhost:8080
```

## Initial admin password location
```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
