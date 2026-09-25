# post: — Actions After Stages Complete

## What it does
Runs steps after all stages have finished — regardless of whether
the pipeline passed or failed. Used for notifications, cleanup,
and publishing results.

## Syntax
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo Building'
            }
        }
    }
    post {
        always {
            echo 'This always runs — pass or fail'
        }
        success {
            echo 'Pipeline passed'
        }
        failure {
            echo 'Pipeline failed — check the logs'
        }
        unstable {
            echo 'Tests ran but some failed'
        }
        changed {
            echo 'Build result changed from last time'
        }
    }
}
```

## post conditions
| Condition | When it runs |
|-----------|-------------|
| `always` | Every time, regardless of result |
| `success` | Only when the pipeline passed |
| `failure` | Only when the pipeline failed |
| `unstable` | When tests ran but some failed |
| `changed` | When result differs from the previous build |

## Post inside a stage
```groovy
stage('Test') {
    steps {
        sh 'npm test'
    }
    post {
        failure {
            echo 'Tests failed in this stage'
        }
    }
}
```

## Key Points
- `post` can sit at pipeline level or inside individual stages
- `always` is useful for cleanup steps that must run regardless
- This is Jenkins' version of GitHub Actions' `if: failure()` and artifacts
- Email notifications and Slack messages typically live in `post { failure }`
- Multiple conditions can be used in the same `post` block

## When I use this
Every real pipeline — at minimum `success` and `failure` blocks
so the team knows when something breaks.
