# A Complete CI Pipeline — Real World Workflow

## What it does
Combines everything from Day 1 and Day 2 into one workflow that
a real project would actually use.

## The complete pipeline
```yaml
name: CI Pipeline

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

env:
  APP_NAME: cloud-devops

jobs:
  # job 1 — run tests on multiple Node versions
  test:
    runs-on: ubuntu-latest
    strategy:
      fail-fast: false
      matrix:
        node: ["18", "20"]

    steps:
      - name: Check out code
        uses: actions/checkout@v4

      - name: Set up Node ${{ matrix.node }}
        uses: actions/setup-node@v4
        with:
          node-version: ${{ matrix.node }}
          cache: "npm"

      - name: Install dependencies
        run: npm ci

      - name: Run tests
        run: npm test

  # job 2 — build only after tests pass
  build:
    needs: test
    runs-on: ubuntu-latest

    steps:
      - name: Check out code
        uses: actions/checkout@v4

      - name: Set up Node
        uses: actions/setup-node@v4
        with:
          node-version: "20"
          cache: "npm"

      - name: Install dependencies
        run: npm ci

      - name: Build
        run: |
          mkdir -p dist
          echo "$APP_NAME build $(date +%F)" > dist/app.txt

      - name: Upload build artifact
        uses: actions/upload-artifact@v4
        with:
          name: app-build
          path: dist/
          retention-days: 7

  # job 3 — deploy only from main after build passes
  deploy:
    needs: build
    if: github.ref == 'refs/heads/main'
    runs-on: ubuntu-latest

    steps:
      - name: Download build artifact
        uses: actions/download-artifact@v4
        with:
          name: app-build

      - name: Deploy
        env:
          TOKEN: ${{ secrets.DEPLOY_TOKEN }}
        run: |
          echo "Deploying $APP_NAME"
          echo "Token length: ${#TOKEN}"
          cat app.txt
```

## What this pipeline does
```
push to main or PR to main
    ↓
test (Node 18) ──┐
test (Node 20) ──┤ parallel
                 ↓
              build ──→ upload artifact
                 ↓
              deploy (main only) ──→ download artifact
```

## Key Points
- Tests run in parallel on Node 18 and 20
- Build only happens after ALL matrix test jobs pass
- Deploy only happens from the main branch
- Artifact passes the build output from build job to deploy job
- Secret is never printed — only its length is echoed for verification
- `fail-fast: false` shows results from all Node versions

## When I use this
This is the baseline for any real Node.js project — adapt it
by replacing the npm commands with your actual build and test commands.
