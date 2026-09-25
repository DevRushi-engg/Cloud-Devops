# when: — Conditional Stages

## What it does
Decides whether a stage runs at all based on a condition.
If the condition is false, the stage is skipped entirely.

## Syntax
```groovy
stage('Deploy') {
    when {
        branch 'main'          // only run on main branch
    }
    steps {
        sh 'echo Deploying to production'
    }
}
```

## Common when conditions
```groovy
// only on main branch
when { branch 'main' }

// only when an environment variable matches
when { environment name: 'DEPLOY_ENV', value: 'production' }

// only when a file exists
when { expression { fileExists('dist/app.txt') } }

// only when triggered by a push (not a timer)
when {
    expression { currentBuild.rawBuild.getCause(
        hudson.triggers.SCMTrigger.SCMTriggerCause) != null
    }
}

// combine conditions — all must be true
when {
    allOf {
        branch 'main'
        environment name: 'DEPLOY', value: 'true'
    }
}

// either condition is enough
when {
    anyOf {
        branch 'main'
        branch 'develop'
    }
}
```

## Full example
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps { sh 'echo Building' }
        }
        stage('Test') {
            steps { sh 'echo Testing' }
        }
        stage('Deploy') {
            when { branch 'main' }
            steps { sh 'echo Deploying to production' }
        }
    }
}
```

## Key Points
- A skipped stage shows as grey in the Stage View — not a failure
- `branch 'main'` is the most common guard on deploy stages
- `when` is evaluated before the stage's `agent` is allocated
- This is Jenkins' equivalent of GitHub Actions' `if: github.ref == 'refs/heads/main'`
- `allOf` and `anyOf` let you combine multiple conditions

## When I use this
Guarding deploy stages so they only run from the main branch,
preventing production deployments from feature branches.
