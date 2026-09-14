# Artifacts — Save Files From a Run

## What it does
Saves files from a workflow run so you can download them later
or pass them between jobs. The runner machine disappears when
the job ends — artifacts are how you get files out.

## Upload an artifact
```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Build the app
        run: mkdir -p dist && echo "app v1.0" > dist/app.txt

      - name: Upload build output
        uses: actions/upload-artifact@v4
        with:
          name: app-build        # artifact name shown in UI
          path: dist/            # file or folder to upload
          retention-days: 7      # how long GitHub keeps it
```

## Download an artifact in another job
```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: echo "output" > result.txt
      - uses: actions/upload-artifact@v4
        with:
          name: result
          path: result.txt

  deploy:
    needs: build               # wait for build job
    runs-on: ubuntu-latest
    steps:
      - uses: actions/download-artifact@v4
        with:
          name: result         # must match upload name
      - run: cat result.txt    # file is now here
```

## Finding artifacts after a run
```
GitHub → Actions tab → click the run → scroll to Artifacts section
→ click the artifact name to download a zip
```

## Key Points
- Runners are ephemeral — files disappear when the job ends
- `upload-artifact` saves files to GitHub's storage
- `download-artifact` retrieves them in a later job
- The artifact `name` must match exactly between upload and download
- Default retention is 90 days — set `retention-days:` to reduce storage
- Artifacts appear in the run summary page — easy to download

## Common artifact use cases
| What to upload | Why |
|----------------|-----|
| `dist/` or `build/` | Compiled app to deploy later |
| Test report HTML | Review test results after the run |
| Coverage reports | Track test coverage over time |
| Log files | Debug a flaky test run |

## When I use this
Saving compiled binaries for the deploy job, uploading test reports,
passing build output from a build job to a deploy job.
