# strategy: matrix: — Test Many Versions in One Run

## What it does
Runs the same job multiple times in parallel, each time with
different values from the matrix. One YAML block, many parallel runs.

## Single dimension matrix
```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node: ["18", "20", "22"]

    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: ${{ matrix.node }}
      - run: node --version
      - run: npm test
```
This creates 3 parallel jobs: one for Node 18, one for 20, one for 22.

## Two dimensional matrix
```yaml
jobs:
  test:
    strategy:
      matrix:
        os: [ubuntu-latest, macos-latest]
        node: ["18", "20"]
    runs-on: ${{ matrix.os }}

    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: ${{ matrix.node }}
      - run: npm test
```
2 × 2 = 4 parallel runs:
- Ubuntu + Node 18
- Ubuntu + Node 20
- macOS + Node 18
- macOS + Node 20

## What it looks like in Actions tab
```
test (ubuntu, node 18) ✅
test (ubuntu, node 20) ✅
test (macos, node 18)  ✅
test (macos, node 20)  ❌  ← catches version-specific bug
```

## fail-fast option
```yaml
strategy:
  fail-fast: false      # keep running other matrix jobs if one fails
  matrix:
    node: ["18", "20", "22"]
```
Default `fail-fast: true` cancels remaining matrix jobs when one fails.
Set to `false` to see results from ALL combinations.

## Key Points
- Matrix values are referenced with `${{ matrix.variable_name }}`
- Each combination gets its own fresh machine and its own log
- Perfect for libraries that support multiple language versions
- Every combination costs runner minutes — keep matrices focused
- `fail-fast: false` is useful when you want full test coverage results

## When I use this
Testing a library across multiple Python or Node versions, verifying
cross-platform compatibility, running the same deploy across environments.
