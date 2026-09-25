# withCredentials — Using Secrets Safely in a Jenkinsfile

## What it does
Injects a stored credential into a pipeline step without
ever writing the value in the Jenkinsfile or printing it in logs.

## Adding a credential in Jenkins
```
1. Manage Jenkins → Credentials
2. Click the appropriate scope (Global)
3. Click "Add Credentials"
4. Kind: Secret text (for tokens), Username with password, SSH key
5. ID: deploy-token   ← the name you reference in the Jenkinsfile
6. Description: GitHub deploy token
7. Paste the value → Save
```

## Using a credential in pipeline steps
```groovy
// secret text (API token, password)
steps {
    withCredentials([string(credentialsId: 'deploy-token', variable: 'TOKEN')]) {
        sh 'echo "Token length: ${#TOKEN}"'
        // use $TOKEN in your actual command
        // sh "curl -H 'Authorization: Bearer $TOKEN' https://api.example.com"
    }
}

// username and password
steps {
    withCredentials([usernamePassword(
        credentialsId: 'dockerhub-creds',
        usernameVariable: 'DOCKER_USER',
        passwordVariable: 'DOCKER_PASS'
    )]) {
        sh 'docker login -u $DOCKER_USER -p $DOCKER_PASS'
    }
}

// SSH key
steps {
    withCredentials([sshUserPrivateKey(
        credentialsId: 'deploy-key',
        keyFileVariable: 'KEY_FILE'
    )]) {
        sh 'ssh -i $KEY_FILE user@server "deploy.sh"'
    }
}
```

## ⚠️ Critical Rules
```groovy
// NEVER do this — prints the secret in plain text
sh 'echo $TOKEN'

// SAFE — print only the length to verify it is set
sh 'echo "Token length: ${#TOKEN}"'
```

## Key Points
- Credentials are stored in Jenkins — never in the Jenkinsfile
- Reference by the ID you assigned when storing the credential
- Jenkins automatically masks the value as `***` in console logs
- Even masked secrets should never be echoed — masking can be bypassed
- `withCredentials` scope limits exposure — variable only exists in that block

## When I use this
Deploying to cloud providers, pushing Docker images, calling
authenticated APIs — anything needing a token or password.
