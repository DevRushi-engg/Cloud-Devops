# Professional Team Git Workflow

## What it is
The daily loop that every professional engineering team follows.
Every step exists for a reason — protecting the team's shared code.

## The Full Workflow
```bash
# 1. start from the latest main
git switch main
git pull

# 2. create a branch for your task
git switch -c feature-x

# 3. work and commit in small logical pieces
nano file.md
git add file.md
git commit -m "feat: add feature x initial setup"
# keep working...
git commit -m "feat: complete feature x"

# 4. push your branch to GitHub
git push -u origin feature-x

# 5. open a PR on GitHub
# write title, description, request a reviewer

# 6. address review feedback
git add .
git commit -m "fix: address review comments"
git push

# 7. after PR is merged — clean up
git switch main
git pull
git branch -d feature-x
git push origin --delete feature-x
```

## Team Rules
| Rule | Why it exists |
|------|--------------|
| main is always deployable | Breaking main blocks everyone |
| Never commit directly to main | Skips review — always branch and PR |
| Never force push a shared branch | Can delete teammates' commits |
| Pull before you start | Builds on latest code |
| Push before you stop | Your work is backed up |

## Handling a conflict while collaborating
```bash
# someone else changed the same file
git pull                    # conflict appears
# edit the file — remove <<<< ==== >>>> markers
# keep the correct combined version
git add app.md
git commit                  # finish the merge
git push
```

## Key Points
- This loop is what you do every single day as an engineer
- Small frequent commits are better than one giant commit at the end
- PR descriptions save your reviewer time — write them well
- Talk to the person whose code conflicts with yours — faster than guessing
- `git log --oneline --graph` after merging shows the full picture

## When I use this
Every working day — this is not an advanced workflow,
it is the baseline for any team using Git.
