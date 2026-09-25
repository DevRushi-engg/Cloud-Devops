# agent — Where the Pipeline Runs

## What it does
Tells Jenkins which machine (controller or agent) should run
the pipeline or an individual stage.

## Syntax
```groovy
// run on any available agent — most common
pipeline {
    agent any
}

// run on an agent with a specific label
pipeline {
    agent { label 'linux' }
}

// no global agent — define per stage
pipeline {
    agent none
    stages {
        stage('Build') {
            agent { label 'build-server' }
            steps {
                sh 'npm run build'
            }
        }
    }
}

// run in a Docker container
pipeline {
    agent {
        docker { image 'node:20' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'node --version'
            }
        }
    }
}
```

## Agent options
| Option | What it does |
|--------|-------------|
| `any` | Run on whichever agent is free |
| `none` | No global agent — each stage must define its own |
| `label 'name'` | Run on agents tagged with that label |
| `docker { image '' }` | Run inside a Docker container |

## Key Points
- `agent any` is the right choice when learning and for simple setups
- `agent none` at pipeline level + `agent` per stage lets different stages
  run on different machines
- Labels are set in Manage Jenkins → Nodes → agent configuration
- Docker agents give you a clean, reproducible build environment
- Without an agent declaration the pipeline will fail to parse

## When I use this
`agent any` for everything while learning.
`agent { label 'linux' }` when the team has specialised build machines.
`agent { docker { image 'node:20' } }` for clean reproducible builds.
