# Your First Complete Workflow — Hello GitHub Actions

## What it does
A minimal working workflow that runs on every push,
checks out the code, and prints information about the run.

## The file
```bash
# create the directory
mkdir -p .github/workflows

# create the file
nano .github/workflows/ci.yml
```

## Minimal workflow
```yaml
name: First CI

on: push

jobs:
  greet:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: echo "Hello from GitHub Actions!"
```

## More complete first workflow
```yaml
name: CI

on: push

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Check out code
        uses: actions/checkout@v4

      - name: Show commit info
        run: echo "Running for commit $GITHUB_SHA"

      - name: List repository files
        run: ls -la

      - name: Show current directory
        run: pwd
```

## Push it and watch it run
```bash
git add .github/workflows/ci.yml
git commit -m "feat: add first CI workflow"
git push
```

Then on GitHub:
1. Click the **Actions** tab
2. See your workflow with a yellow dot (running)
3. Click it to see each step's live log output
4. Green check = success, red X = a step failed

## Reading the Actions tab
```
Actions tab
└── CI (workflow name)
    └── push: feat: add first CI workflow (run)
        └── build (job)
            ├── ✅ Check out code
            ├── ✅ Show commit info
            ├── ✅ List repository files
            └── ✅ Show current directory
```

## Key Points
- The YAML file must be in `.github/workflows/` — exact path
- Two spaces per indentation level — no tabs
- Every workflow needs: name, on, jobs, runs-on, steps
- `actions/checkout@v4` is always step one
- A failing workflow caught a problem — it is doing its job

## When I use this
This is the starting point for every project — push this first,
confirm it works, then build from here.
