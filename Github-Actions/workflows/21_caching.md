# Caching — Speed Up Workflows by Reusing Dependencies

## What it does
Saves downloaded dependencies (like node_modules) between runs
so they do not need to be re-downloaded every time.
Slow CI is skipped CI — caching keeps it fast.

## Built-in cache with setup-node
```yaml
steps:
  - uses: actions/checkout@v4

  - uses: actions/setup-node@v4
    with:
      node-version: "20"
      cache: "npm"           # built-in cache for npm

  - run: npm ci              # uses cache if lock file unchanged
  - run: npm test
```

## Manual cache with actions/cache
```yaml
steps:
  - uses: actions/checkout@v4

  - name: Cache node_modules
    uses: actions/cache@v4
    with:
      path: ~/.npm
      key: ${{ runner.os }}-node-${{ hashFiles('package-lock.json') }}
      restore-keys: |
        ${{ runner.os }}-node-

  - run: npm ci
  - run: npm test
```

## Cache for Python
```yaml
- uses: actions/setup-python@v5
  with:
    python-version: "3.12"
    cache: "pip"

- run: pip install -r requirements.txt
```

## How cache keys work
```
key: ubuntu-node-abc123def456    ← hash of package-lock.json
```
- If `package-lock.json` changes → new hash → cache miss → re-download
- If `package-lock.json` unchanged → same hash → cache hit → skip download

## Key Points
- `cache: "npm"` in `setup-node` is the easiest way — one line
- Cache hit saves 30-60 seconds on most projects
- Cache is keyed by a hash of the lock file — automatically invalidates when deps change
- `npm ci` is faster than `npm install` and respects the lock file — use it in CI
- Cache storage is free up to 10GB per repo

## When I use this
Every workflow that installs dependencies — which is almost every
real workflow. Always add caching to avoid paying for re-downloads.
