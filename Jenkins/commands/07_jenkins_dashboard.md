# Jenkins Dashboard — The Control Room

## What it is
The main screen you see after logging in.
Lists every job with its most recent build result.
Every Jenkins action starts from here.

## Dashboard layout
```
Jenkins Dashboard
├── Left Sidebar
│   ├── New Item          — create a new job
│   ├── People            — users who have triggered builds
│   ├── Build History     — every build across all jobs
│   ├── Manage Jenkins    — server-wide settings
│   └── My Views          — custom filtered views
│
└── Main Area
    └── Job list with build status indicators
        ✅ Blue ball   = last build succeeded
        ❌ Red ball    = last build failed
        ⚪ Grey ball   = never built
        🔵 Spinning    = currently building
```

## Build status colours
| Colour | Meaning |
|--------|---------|
| Blue ball | Success — counterintuitive but correct |
| Red ball | Failed |
| Grey ball | Not built yet |
| Yellow ball | Unstable — tests ran but some failed |

Blue for success is a leftover from Jenkins' original name Hudson —
it surprises almost everyone the first time.

## Key navigation
| Where | What you do there |
|-------|-----------------|
| New Item | Create a new job of any type |
| Manage Jenkins | Plugins, system settings, security, nodes |
| Build History | Timeline of every recent build |
| Job name click | Opens that job's own page |
| Build number click | Opens that specific build's details |

## Key Points
- The dashboard updates automatically as builds run
- A spinning blue circle on a build number means it is running right now
- Click any job name to see its configuration and build history
- Click any build number to see its Console Output
- The dashboard is the screen you return to constantly

## When I use this
Every time I open Jenkins — this is the starting point for
creating jobs, checking build results, and navigating to settings.
