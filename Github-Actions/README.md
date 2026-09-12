# GitHub Actions

This folder contains my learning notes from the GitHub Actions module
of the deboistech Multi-Cloud Engineering cohort.

## What is GitHub Actions?
GitHub Actions is a CI/CD platform built directly into GitHub.
It runs automated workflows on GitHub's servers whenever Git events
happen — like a push or a pull request opening.
You define the automation in YAML files stored in your repository.

## What is in this folder?
- `workflows/` — example workflow YAML files
- `sessions/` — session summaries covering what was taught each day

## Module Structure
| Day | Topic |
|-----|-------|
| Day 1 | CI/CD concepts, workflow structure, first workflow |

## Key Concepts
- **Workflow** — the whole automated process, one `.yml` file
- **Job** — a group of steps running on one machine
- **Step** — a single task, run a command or use an action
- **Action** — a reusable prebuilt unit from the marketplace

## Workflow files live here
```
.github/workflows/ci.yml
```
