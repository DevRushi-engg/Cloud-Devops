# environment: — Variables in a Jenkinsfile

## What it does
Defines environment variables available to shell commands in
your pipeline. Can be set at pipeline level or stage level.
Stage-level values override pipeline-level values.

## Syntax
```groovy
pipeline {
    agent any

    // pipeline level — available to ALL stages
    environment {
        APP_NAME = 'cloud-devops'
        VERSION  = '1.0.0'
    }

    stages {
        stage('Build') {
            // stage level — available to THIS stage only
            environment {
                BUILD_MODE = 'production'
            }
            steps {
                sh 'echo "$APP_NAME $VERSION $BUILD_MODE"'
            }
        }
        stage('Test') {
            steps {
                // APP_NAME and VERSION available here
                // BUILD_MODE is NOT available here
                sh 'echo "Testing $APP_NAME"'
            }
        }
    }
}
```

## Built-in Jenkins variables available in every pipeline
| Variable | What it holds |
|----------|-------------|
| `BUILD_NUMBER` | The current build number: 1, 2, 3 |
| `JOB_NAME` | Name of this Jenkins job |
| `WORKSPACE` | Path to the checked-out code |
| `GIT_COMMIT` | Commit hash that triggered the build |
| `GIT_BRANCH` | Branch that triggered the build |
| `BUILD_URL` | Direct URL to this build's page |

## Using variables in shell commands
```groovy
steps {
    sh '''
        echo "App: $APP_NAME"
        echo "Build: $BUILD_NUMBER"
        echo "Commit: $GIT_COMMIT"
        echo "Workspace: $WORKSPACE"
    '''
}
```

## Key Points
- Variable names use ALL_CAPS by convention
- Values are strings — no quotes needed around simple values
- Use single quotes in `sh` to let the shell expand the variables
- Stage-level `environment` block overrides pipeline-level for that stage
- Never put secret values directly here — use `withCredentials` instead

## When I use this
Setting app name, version, environment name — anything referenced
in multiple stages or that makes the pipeline self-documenting.
