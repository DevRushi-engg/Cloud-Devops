# checkout scm — Checking Out the Triggering Commit

## What it does
Checks out the exact commit that triggered the current build
into the workspace. The pipeline-specific way to clone your repo.

## Syntax
```groovy
stage('Checkout') {
    steps {
        checkout scm
    }
}
```

## checkout scm vs actions/checkout
| Jenkins | GitHub Actions |
|---------|---------------|
| `checkout scm` | `uses: actions/checkout@v4` |
| Auto-configured from Pipeline SCM settings | Needs to be explicit |
| Checks out triggering commit | Checks out triggering commit |

## When you need it explicitly
```groovy
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm          // clone the repo
            }
        }
        stage('Build') {
            steps {
                sh 'ls -la'           // files are available now
                sh 'cat README.md'
            }
        }
    }
}
```

## Key Points
- When "Pipeline script from SCM" is set, checkout happens automatically
  before your first stage — you often do not need to call it explicitly
- Call it explicitly when `agent none` is used at the pipeline level and
  each stage has its own agent
- `checkout scm` is smart — it uses the SCM settings from the job config
- After checkout, all your repo files are available in `$WORKSPACE`

## When I use this
In pipelines with `agent none` where checkout needs to happen in a
specific stage, or when I want to make the checkout step explicit
and visible in the Stage View.
