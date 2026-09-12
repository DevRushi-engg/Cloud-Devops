# GitHub Actions — CI/CD Built Into GitHub

## What it is
GitHub Actions is a CI/CD platform built directly into GitHub.
It runs your commands on GitHub's servers whenever Git events happen.
You describe the automation in a YAML file stored in your repo.

## Why GitHub Actions
| Reason | Detail |
|--------|--------|
| Lives where your code is | No extra accounts or tools to set up |
| Triggered by Git events | push, pull_request — events you already use |
| Huge marketplace | Thousands of prebuilt actions to reuse |
| Free for public repos | Generous free tier for private repos |

## How it works
```
1. You push a YAML file to .github/workflows/
2. GitHub detects the file
3. On the next matching event (like a push), GitHub runs it
4. Commands execute on a fresh GitHub-hosted machine
5. Results appear in the Actions tab
```

## Key Points
- Push a YAML file and GitHub starts automating — that is the whole idea
- Free for public repos, generous minutes for private repos
- No separate tool to install or account to create
- The YAML file IS the pipeline — it lives in your repo like any other file
- Actions tab on GitHub is your control room — every run and log lives there

## Git vs GitHub Actions
| Git | GitHub Actions |
|-----|---------------|
| Tracks changes | Reacts to changes |
| You run commands | GitHub runs commands |
| Local tool | GitHub's cloud |

## When I use this
Every project that needs automated testing, linting, building,
or deploying — which is every real project.
