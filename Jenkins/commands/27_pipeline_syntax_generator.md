# Pipeline Syntax Generator — Let Jenkins Write the Groovy

## What it is
A built-in tool inside every Pipeline job that generates the
correct Groovy syntax for any pipeline step.
Pick a step from a dropdown, fill in a form, get the code.

## How to access it
```
1. Open any Pipeline job in Jenkins
2. Click "Pipeline Syntax" in the left sidebar
3. Select a step from the "Sample Step" dropdown
4. Fill in the form fields
5. Click "Generate Pipeline Script"
6. Copy the output into your Jenkinsfile
```

## Common steps to generate with it
| Step to generate | What you get |
|-----------------|-------------|
| `withCredentials` | The exact credential binding syntax |
| `sh` | Shell step with options |
| `checkout scm` | The SCM checkout step |
| `archiveArtifacts` | Artifact archiving step |
| `junit` | JUnit test results publishing |
| `emailext` | Extended email notification |

## Example — generating withCredentials
```
1. Select: withCredentials: Bind credentials to variables
2. Add Binding: Secret text
3. Variable: TOKEN
4. Credentials: select deploy-token from the list
5. Click "Generate Pipeline Script"

Output:
withCredentials([string(credentialsId: 'deploy-token', variable: 'TOKEN')]) {
    // some block
}
```

## Key Points
- Use this whenever you are unsure of the exact syntax for a step
- It is the fastest way to get credential binding syntax exactly right
- Generated code can be pasted directly into the Jenkinsfile
- The Declarative Directive Generator is the same idea for pipeline blocks
- Only shows steps for plugins that are installed

## When I use this
Any time I need a step I have not written before — especially
`withCredentials`, `archiveArtifacts`, and notification steps.
