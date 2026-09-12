# steps:, run:, uses: — Defining Steps

## What it does
`steps:` is a list of tasks that run in order inside a job.
`run:` executes a shell command.
`uses:` pulls in a prebuilt action from the marketplace.

## Syntax
```yaml
steps:
  # run a shell command
  - name: Say hello
    run: echo "Hello from Actions"

  # run multiple commands
  - name: Setup and check
    run: |
      echo "Line one"
      ls -la
      pwd

  # use a prebuilt action
  - uses: actions/checkout@v4

  # use an action with settings
  - uses: actions/setup-node@v4
    with:
      node-version: "20"
```

## run: vs uses:
| | `run:` | `uses:` |
|-|--------|---------|
| What it runs | Shell command | Prebuilt marketplace action |
| Example | `run: npm test` | `uses: actions/checkout@v4` |
| You write | The command | The action name and version |

## Multi-line run with pipe
```yaml
# | allows multiple lines
- name: Install and test
  run: |
    npm install
    npm run build
    npm test
```

## Key Points
- Every step starts with a `-` dash
- `name:` is optional but makes logs much easier to read — always add it
- Steps run in the order listed — top to bottom
- If any step fails (non-zero exit code) the job stops there
- `uses:` always pins a version with `@v4` — never use floating versions
- `with:` passes settings (parameters) to an action

## When I use this
Building every step of a workflow — combining `run:` commands
for custom logic with `uses:` for standard tasks like checkout.
