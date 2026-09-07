# Pull Requests In Depth — Opening, Reviewing, Merging

## What it is
A Pull Request asks teammates to review your branch before
it merges into main. It is where code review, discussion,
and automated tests all happen.

## Opening a PR
```bash
# 1. start from latest main
git switch main && git pull

# 2. create your branch and do the work
git switch -c feature-about
echo "## About" >> README.md
git add README.md
git commit -m "docs: add About section to README"

# 3. push the branch
git push -u origin feature-about

# 4. on GitHub — click "Compare & pull request"
# 5. write a clear title and description
# 6. request a reviewer
# 7. click "Create pull request"
```

## Good PR description template
```markdown
## What this does
Adds an About section to the README explaining the repo purpose.

## Why
The README had no context for new visitors.

## How to test
Open README.md and confirm the About section appears
with correct content.
```

## Good PR vs Bad PR
| Good PR | Bad PR |
|---------|--------|
| One focused change | Ten unrelated changes |
| Under 400 lines | 3000 lines nobody reads |
| Explains the why | Title says "update" |
| Tests pass | Pushed broken code |

## Reviewing a PR
1. Open the PR and click the **Files changed** tab
2. Click any line to leave a comment
3. Choose: **Comment**, **Approve**, or **Request changes**
4. Be kind and specific — explain why, not just what

```
✅ "This could break if the input is empty — worth adding a check"
❌ "You forgot error handling"
```

## Three merge options on GitHub
| Option | What it does |
|--------|-------------|
| Merge commit | Keeps every commit plus adds a merge node |
| Squash and merge | All commits become one tidy commit |
| Rebase and merge | Replays commits, no merge node |

Squash and merge is the most common on teams — ten "fix typo"
commits become one meaningful entry in main's history.

## Key Points
- Nobody pushes straight to main on a professional team
- A PR creates a permanent record of what changed and why
- Small PRs get reviewed fast — huge ones sit for days
- You can keep pushing to the same branch — the PR updates automatically

## When I use this
Every time I finish work on a feature branch — this is the
standard way professional teams ship code.
