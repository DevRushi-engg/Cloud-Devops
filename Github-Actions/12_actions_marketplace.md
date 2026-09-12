# Actions Marketplace — Prebuilt Actions to Reuse

## What it is
Thousands of prebuilt actions shared by GitHub and the community.
Find them at github.com/marketplace/actions.
Plug them into your workflow with `uses:`.

## Essential actions you will use constantly
```yaml
# get your code onto the runner
- uses: actions/checkout@v4

# install Node.js
- uses: actions/setup-node@v4
  with:
    node-version: "20"

# install Python
- uses: actions/setup-python@v5
  with:
    python-version: "3.12"

# upload a file as a downloadable artifact
- uses: actions/upload-artifact@v4
  with:
    name: build-output
    path: dist/

# cache dependencies for faster runs
- uses: actions/cache@v4
  with:
    path: ~/.npm
    key: ${{ runner.os }}-node-${{ hashFiles('package-lock.json') }}
```

## How to find actions
1. Go to github.com/marketplace/actions
2. Search for what you need (e.g. "deploy to AWS S3")
3. Check the star count and last updated date
4. Read the README before using it
5. Pin the version with `@v4` or `@v3`

## Vetting an action before use
```yaml
# GOOD — official GitHub action, high trust
- uses: actions/checkout@v4

# CHECK before using — third party
# verify: star count, recent commits, known publisher
- uses: some-company/deploy-action@v2
```

## Key Points
- Official GitHub actions (`actions/`) are fully trusted
- Third-party actions can read your environment and secrets — vet them
- Always pin with `@v4` not `@latest` — reproducible and safe
- `with:` passes input parameters to the action
- Popular actions have thousands of stars and clear documentation

## When I use this
Any time I need a standard task — language setup, deployment,
caching, notifications — the marketplace has it ready.
