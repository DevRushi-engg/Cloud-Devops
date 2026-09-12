# What is CI/CD — Continuous Integration and Continuous Delivery

## What it is
CI/CD is the practice of automating the testing and delivery
of code every time a change is pushed.

## CI vs CD
| | CI | CD |
|-|----|----|
| Stands for | Continuous Integration | Continuous Delivery |
| What it does | Test every change automatically | Ship every good change automatically |
| When it runs | On every push | After CI passes |

## The Pipeline
```
push → build → test → deploy
code
```
Each stage runs only if the one before it passed.
A red X anywhere stops the pipeline — broken code never ships.

## Why it matters
| Without CI/CD | With CI/CD |
|--------------|-----------|
| Push code, manually run tests if you remember | Every push is tested automatically |
| Teammate's change breaks the build, nobody notices for days | Bug caught in minutes |
| Deploying means a checklist at 2am | Merge triggers automatic deploy |
| Humans forget steps | Machines never do |

## Key Points
- Every manual step is a step someone will eventually skip
- CI catches bugs in minutes not days
- CD means code that passes tests is automatically delivered
- GitHub Actions is how we build CI/CD inside GitHub

## When I use this
Understanding this mental model is the foundation for every
GitHub Actions workflow I will write.
