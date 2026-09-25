# Jenkinsfile — Pipeline as Code

## What it is
A text file named exactly `Jenkinsfile` placed at the root of
your repository. Jenkins reads it and runs whatever it describes.
Your pipeline lives with your code — versioned, reviewable, shareable.

## Why Pipeline as Code beats Freestyle
| Freestyle | Pipeline (Jenkinsfile) |
|-----------|----------------------|
| Settings live inside Jenkins only | File lives in your Git repo |
| Invisible to teammates | Reviewed in pull requests like any code |
| No version history | Full change history in Git |
| Hard to reproduce | Same file = same pipeline every time |

## Creating the file
```bash
# at the root of your repo
nano Jenkinsfile

# no file extension — just the one word
# commit it
git add Jenkinsfile
git commit -m "feat: add Jenkinsfile"
git push
```

## Key Points
- The filename must be exactly `Jenkinsfile` — capital J, no extension
- Place it at the root of the repository — not in a subfolder
- Jenkins fetches it automatically when you set "Pipeline script from SCM"
- Change the pipeline by editing the file and pushing — same as any code
- The file is Groovy syntax — but you only need a small subset of it

## Declarative vs Scripted
| Declarative | Scripted |
|-------------|---------|
| Fixed predictable structure | Full Groovy code |
| Easier to read and learn | More powerful, harder to get right |
| `pipeline { }` wrapper | `node { }` wrapper |
| What almost every team uses | Legacy — you will read it but rarely write it |

## When I use this
Every Jenkins project that goes beyond a quick test — which means
every real project from here forward.
