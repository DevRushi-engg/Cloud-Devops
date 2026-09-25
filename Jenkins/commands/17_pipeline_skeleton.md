# Declarative Pipeline Skeleton — agent, stages, steps

## What it is
The required minimum structure every declarative Jenkinsfile needs.
Three nested blocks: `pipeline`, `stages`, and at least one `stage`.

## The minimum valid pipeline
```groovy
pipeline {
    agent any
    stages {
        stage('Example') {
            steps {
                echo 'Hello from Jenkins Pipeline'
            }
        }
    }
}
```

## What each block does
| Block | What it is |
|-------|-----------|
| `pipeline { }` | The outer wrapper — everything goes inside |
| `agent any` | Run on any available Jenkins agent |
| `stages { }` | Container for all your stage blocks |
| `stage('Name') { }` | One logical phase — Build, Test, Deploy |
| `steps { }` | The actual commands inside a stage |

## A three-stage pipeline
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'ls -la'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'echo All tests passed'
            }
        }
        stage('Done') {
            steps {
                echo 'Pipeline complete'
            }
        }
    }
}
```

## Key Points
- Every declarative pipeline needs exactly: `pipeline`, `agent`, `stages`
- At least one `stage` is required inside `stages`
- Stage names appear as columns in the Stage View — make them descriptive
- Braces must be balanced — one missing `}` breaks the whole pipeline
- `echo` prints to the console log — useful for debugging
- `sh` runs a shell command — the main way to do real work

## When I use this
This skeleton is copy-pasted as the starting point for every
new Jenkinsfile — fill in the stages from there.
