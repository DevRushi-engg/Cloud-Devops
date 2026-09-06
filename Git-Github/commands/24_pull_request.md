# Pull Request — Review Before Merging

## What it is
A Pull Request (PR) is a GitHub feature — not a Git command.
It says: here is my branch, please review and merge it into main.
It is a conversation about your code before it joins the main branch.

## Pull Request Workflow
```bash
# 1. create a branch and do your work
git switch -c feature-login

# 2. commit your changes
git add .
git commit -m "feat: add login feature"

# 3. push the branch to GitHub
git push -u origin feature-login

# 4. on GitHub — click "Compare & pull request"
# 5. write a title and description
# 6. teammates review, you fix, then it gets merged
# 7. delete the branch after merge
git branch -d feature-login
git push origin --delete feature-login
```

## What a good PR description includes
```
## What this does
Adds login validation to the signup form.

## Why
Users were able to submit empty email fields causing 500 errors.

## How to test
1. Go to /signup
2. Submit with empty email
3. Should see validation error, not 500
```

## Key Points
- A PR is a GitHub feature — not part of Git itself
- Small PRs get reviewed fast — huge ones sit for days
- Always describe what changed AND why
- You can keep pushing to the same branch — PR updates automatically
- After merge, delete the branch to keep the repo clean
- `Compare & pull request` button appears on GitHub after pushing a branch

## When I use this
Every time I finish a feature branch and want it reviewed
before it goes into main — this is how professional teams ship code.
