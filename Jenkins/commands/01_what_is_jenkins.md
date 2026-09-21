# What is Jenkins — Self-Hosted CI/CD Automation Server

## What it is
Jenkins is an open source automation server you install and run
on your own machine or company server. It watches your repository
and runs jobs automatically when something changes.

## GitHub Actions vs Jenkins
| | GitHub Actions | Jenkins |
|-|---------------|---------|
| Runs on | GitHub's cloud | A server you install and manage |
| Setup | Just a YAML file | Install the server, then configure |
| Config format | YAML | Groovy (Jenkinsfile) or click-through UI |
| Ecosystem | Growing marketplace | Huge mature plugin library |
| Code leaves your servers | Yes | No — stays on your infrastructure |

## Why Jenkins still matters
- Self-hosted: your code and builds never leave your own servers
- Enterprises with strict compliance rules require self-hosted CI
- A plugin ecosystem built over more than a decade of real use
- Countless existing pipelines at established companies run on it
- Very likely you will meet Jenkins at your first job

## Key Points
- Jenkins started as a project called Hudson in 2004
- Same CI/CD concepts as GitHub Actions — different tool and location
- Neither is strictly better — teams choose based on their needs
- If you understand CI/CD once, you understand it in every tool

## When I use this
When working at a company that requires self-hosted CI for
compliance, security, or because their pipeline already runs on it.
