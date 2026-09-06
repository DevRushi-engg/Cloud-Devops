# README & Markdown — Document Your Project

## What it is
`README.md` is the front page of your GitHub repository.
It is shown automatically when anyone visits your repo page.
Written in Markdown — plain text with simple formatting.

## Create a README
```bash
nano README.md
git add README.md
git commit -m "docs: add project README"
git push
```

## What goes in a README
```markdown
# Project Name
One line saying what it does and why it exists.

## Installation
Steps to get it running.

## Usage
How to use it with examples.

## Contributing
How others can help.

## License
What people can do with your code.
```

## Markdown Essentials
| Syntax | What it produces |
|--------|----------------|
| `# Heading 1` | Large heading |
| `## Heading 2` | Medium heading |
| `### Heading 3` | Small heading |
| `**bold**` | **bold** |
| `*italic*` | *italic* |
| `- item` | Bullet point |
| `1. item` | Numbered list |
| `` `code` `` | Inline code |
| ` ```bash ``` ` | Code block with syntax highlight |
| `[text](url)` | Clickable link |
| `![alt](image.url)` | Image |

## My Terminal Output
```bash
rushi@rushi:~/Cloud-Devops$ cat README.md
# Cloud-Devops Learning Repo
Documenting my journey through the deboistech Multi-Cloud cohort.

## What is in this repo
- Linux/ — command notes from Days 1-5
- Git-GitHub/ — Git and GitHub notes

rushi@rushi:~/Cloud-Devops$ git add README.md
rushi@rushi:~/Cloud-Devops$ git commit -m "docs: update README"
rushi@rushi:~/Cloud-Devops$ git push
```

## Key Points
- GitHub renders Markdown automatically — preview before committing
- A missing README makes a project look abandoned
- Answer three questions: what is it, how do I run it, how do I help
- Your GitHub profile is a public portfolio — good READMEs matter
- Use code blocks with language tags for syntax highlighting

## When I use this
Every single project gets a README — it is the first file I create
after `git init` and `.gitignore`.
