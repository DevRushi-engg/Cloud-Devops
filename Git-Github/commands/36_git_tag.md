# git tag — Mark a Release Version

## What it does
Creates a permanent bookmark on a specific commit.
Used to mark version releases like v1.0, v2.1.3.
Unlike branches, tags never move.

## Syntax
```bash
git tag -a v1.0 -m "First release"      # create annotated tag
git tag                                  # list all tags
git push origin v1.0                     # push one tag
git push origin --tags                   # push all tags
git tag -d v1.0                          # delete local tag
git push origin --delete v1.0           # delete remote tag
```

## My Terminal Output
```bash
rushi@rushi:~/Cloud-Devops$ git tag -a v1.0 -m "Linux module complete"
rushi@rushi:~/Cloud-Devops$ git tag
v1.0

rushi@rushi:~/Cloud-Devops$ git push origin v1.0
Enumerating objects: 1, done.
To git@github.com:DevRushi-engg/Cloud-Devops.git
 * [new tag] v1.0 -> v1.0
```

## Annotated vs lightweight tags
| Type | Command | Has message | Best for |
|------|---------|-------------|---------|
| Annotated | `git tag -a v1.0 -m "msg"` | Yes | Releases |
| Lightweight | `git tag v1.0` | No | Personal bookmarks |

## Key Points
- Tags are NOT pushed automatically with `git push` — push them explicitly
- GitHub turns pushed tags into Releases automatically
- Semantic versioning: `v1.0.0` = major.minor.patch
- Use `git show v1.0` to see what commit a tag points to
- Tags are permanent references — they mark a moment in history

## Semantic versioning guide
| Version | When to use |
|---------|------------|
| `v1.0.0` | Major release, breaking changes |
| `v1.1.0` | New features, backwards compatible |
| `v1.1.1` | Bug fixes only |

## When I use this
Marking a stable version of a project for release, creating
a checkpoint before a big refactor.
