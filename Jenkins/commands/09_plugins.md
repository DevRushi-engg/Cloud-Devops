# Jenkins Plugins — Extending What Jenkins Can Do

## What it is
Plugins add capabilities Jenkins does not have on its own.
A fresh Jenkins install with zero plugins can do very little.
The suggested plugins from setup cover most day-to-day needs.

## Installing a new plugin
```
1. Dashboard → Manage Jenkins → Plugins
2. Click the "Available plugins" tab
3. Search for the plugin by name
4. Check its checkbox
5. Click Install
6. Restart Jenkins if the plugin requires it
```

## Essential plugins to know
| Plugin | What it adds |
|--------|-------------|
| Git | Clone and track Git repositories |
| Pipeline | Jenkinsfile-based pipeline jobs |
| GitHub | GitHub webhook integration |
| Docker | Build and push Docker images |
| Credentials | Securely store passwords and tokens |
| Blue Ocean | Modern visual pipeline UI |
| Email Extension | Richer email notifications |

## Key Points
- The Git plugin is needed for almost every real job
- If a job type or build step is missing, the fix is almost always a plugin
- Plugins can be updated from Manage Jenkins → Plugins → Updates tab
- Some plugins require a Jenkins restart to activate
- Only install plugins from the official Jenkins marketplace
- A plugin with millions of installs and recent updates is a safe choice

## When I use this
Whenever a feature is missing from a job — GitHub webhook integration,
Docker support, Slack notifications — there is almost certainly a plugin.
