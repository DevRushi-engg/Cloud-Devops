# Jenkins Job Types — Freestyle, Pipeline, Multibranch

## What it is
Jenkins offers several types of jobs. Each suits a different
level of complexity and team maturity.

## Job types comparison
| Type | What it is for |
|------|---------------|
| Freestyle project | Simple click-through jobs — good for learning |
| Pipeline | Build defined as code in a Jenkinsfile |
| Multibranch Pipeline | Automatically builds every branch it finds |
| Folder | Organizes many jobs into groups |
| Multi-configuration | Matrix builds across environments |

## Freestyle project
```
Good for:  Learning, quick tasks, simple automation
Configured: By clicking through the Jenkins UI
Lives:      Inside Jenkins — not in your repo
Weakness:   Hard to version control, hard to review changes
```

## Pipeline project
```
Good for:  Real team projects, complex workflows
Configured: In a Jenkinsfile committed to your repo
Lives:      In your Git repository alongside the code
Strength:   Version controlled, reviewable, reproducible
```

## A first look at a Jenkinsfile
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo Building...'
            }
        }
        stage('Test') {
            steps {
                sh 'echo Running tests...'
            }
        }
    }
}
```
This entire pipeline lives in one file committed right alongside
your code — that is the big difference from Freestyle.

## Multibranch Pipeline
```
Jenkins scans your repo for branches that have a Jenkinsfile
Creates a separate job for each branch automatically
When you create a feature branch with a Jenkinsfile it appears
```

## Key Points
- Start with Freestyle to learn Jenkins
- Move to Pipeline for any real project — it is what teams use
- Multibranch Pipeline is the standard for repos with many developers
- Folder is just an organiser — not a job type that builds anything
- Today: Freestyle. Tomorrow: Pipeline as Code

## When I use this
Freestyle for learning and simple tasks now.
Pipeline jobs for everything real starting the next session.
