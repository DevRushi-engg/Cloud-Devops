# stages, stage, steps — Building the Pipeline Body

## What it does
`stages` is the container for all your stage blocks.
`stage` defines one logical phase with a human-readable name.
`steps` contains the actual commands that run in that phase.

## Syntax
```groovy
stages {
    stage('Build') {
        steps {
            sh 'echo Building'
            sh 'npm install'
            sh 'npm run build'
        }
    }
    stage('Test') {
        steps {
            sh 'npm test'
        }
    }
    stage('Deploy') {
        steps {
            sh 'echo Deploying'
        }
    }
}
```

## Commands available inside steps
| Command | What it does |
|---------|-------------|
| `sh 'command'` | Run a shell command on Linux/macOS |
| `bat 'command'` | Run a batch command on Windows |
| `echo 'text'` | Print to the console log |
| `checkout scm` | Check out the triggering commit |
| `withCredentials([...])` | Use a stored secret safely |

## Multi-line shell commands
```groovy
steps {
    sh '''
        echo "Starting build"
        npm install
        npm run build
        ls -la dist/
    '''
}
```

## Key Points
- Stage names appear as columns in the Stage View — use clear names
- Each `stage` runs in sequence by default — top to bottom
- A failed step stops the current stage and marks the build as FAILED
- `sh` is the most-used command — same as Execute Shell in Freestyle
- Triple-quoted strings `'''` allow multi-line shell scripts
- Stage names are strings — they can contain spaces

## When I use this
Every Jenkinsfile has at least one stage — this is where the
actual work of checkout, build, test, and deploy happens.
