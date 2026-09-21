# Manage Jenkins — Server-Wide Settings

## What it is
The control panel for the entire Jenkins server — not just
one job. Every server-wide configuration lives here.

## Accessing it
```
Dashboard → Manage Jenkins (left sidebar)
```

## Key sections inside Manage Jenkins
| Section | What you do there |
|---------|-----------------|
| Plugins | Install, update, or remove capabilities |
| System | Global settings — tool paths, environment variables |
| Security | Who can log in and what they are allowed to do |
| Nodes | View and manage controller and agent machines |
| Credentials | Store passwords, SSH keys, tokens securely |
| System Log | Jenkins server logs for debugging |

## Key Points
- Almost every server-wide change happens somewhere inside here
- Restart Jenkins from here after installing plugins that require it
- Credentials stored here are available to all jobs — more secure than
  putting them directly in job configuration
- System logs here are useful when Jenkins itself is misbehaving

## When I use this
Installing a new plugin, adding agent machines, storing
credentials, changing global tool paths.
