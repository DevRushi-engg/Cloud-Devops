# A Complete Real Jenkinsfile — Checkout, Build, Test, Deploy

## What it is
A Jenkinsfile that combines all the concepts from Day 2 into
one production-ready pipeline.

## The complete Jenkinsfile
```groovy
pipeline {
    agent any

    environment {
        APP_NAME = 'cloud-devops'
        VERSION  = '1.0.0'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo "Building ${APP_NAME} v${VERSION}"
                echo "Commit: ${GIT_COMMIT}"
            }
        }

        stage('Build') {
            steps {
                sh '''
                    echo "=== Build Stage ==="
                    pwd
                    ls -la
                    echo "Build number: $BUILD_NUMBER"
                '''
            }
        }

        stage('Test') {
            steps {
                sh '''
                    echo "=== Test Stage ==="
                    echo "Running tests for $APP_NAME"
                    echo "All tests passed"
                '''
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                withCredentials([string(credentialsId: 'deploy-token', variable: 'TOKEN')]) {
                    sh '''
                        echo "=== Deploy Stage ==="
                        echo "Token length: ${#TOKEN}"
                        echo "Deploying $APP_NAME to production"
                    '''
                }
            }
        }
    }

    post {
        always {
            echo "Pipeline finished — Build #${BUILD_NUMBER}"
        }
        success {
            echo "SUCCESS: ${APP_NAME} v${VERSION} built and tested"
        }
        failure {
            echo "FAILURE: Check console output at ${BUILD_URL}"
        }
    }
}
```

## Push and run it
```bash
# place Jenkinsfile at root of repo
git add Jenkinsfile
git commit -m "feat: add complete Jenkinsfile pipeline"
git push
```

## What this pipeline does
```
Checkout → Build → Test → Deploy (main only)
                              ↓
                        post: always + success/failure
```

## Key Points
- `agent any` runs on whatever is free
- `environment` block at pipeline level shares vars across all stages
- `checkout scm` gets the exact triggering commit
- `when { branch 'main' }` guards the deploy stage
- `withCredentials` keeps the token out of logs
- `post` block notifies team regardless of outcome

## When I use this
This is the starting template for every new Jenkins project —
adapt the stage commands to the actual build and test tools.
