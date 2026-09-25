# Creating a Pipeline Project — Connecting to Your Jenkinsfile

## What it does
Creates a Jenkins Pipeline job that fetches and runs your
Jenkinsfile from your Git repository automatically.

## Creating the Pipeline project
```
1. Dashboard → New Item
2. Enter a name: demo-pipeline
3. Select "Pipeline" (not Freestyle)
4. Click OK
5. Scroll to the "Pipeline" section at the bottom
```

## Pipeline section configuration
```
Definition:        Pipeline script from SCM
SCM:               Git
Repository URL:    https://github.com/DevRushi-engg/Cloud-Devops.git
Credentials:       None (for a public repo)
Branch Specifier:  */main
Script Path:       Jenkinsfile
```

## Pipeline script vs Pipeline script from SCM
| Option | What it does |
|--------|-------------|
| Pipeline script | Paste Jenkinsfile directly into Jenkins UI |
| Pipeline script from SCM | Jenkins fetches it from your repo |

Always use "Pipeline script from SCM" for real projects — the file
lives with the code, not buried inside Jenkins.

## Running the pipeline
```
1. Click Save
2. Click "Build Now" in the left sidebar
3. Watch the Stage View appear below Build History
4. Each stage shows as a column — green = passed, red = failed
5. Click any stage column to see that stage's log
```

## Key Points
- Choose "Pipeline" not "Freestyle" when creating the item
- "Pipeline script from SCM" is the most important dropdown on the page
- Script Path is just `Jenkinsfile` since it sits at the repo root
- Jenkins clones the repo, reads the Jenkinsfile, and runs it
- The Stage View is Jenkins' answer to GitHub Actions' job summary

## Stage View colours
| Colour | Meaning |
|--------|---------|
| Green | Stage passed |
| Red | Stage failed |
| Grey | Stage was skipped |
| Blue spinning | Stage is running right now |

## When I use this
Every new Jenkins project — this replaces Freestyle for any
project where the pipeline should be version controlled.
