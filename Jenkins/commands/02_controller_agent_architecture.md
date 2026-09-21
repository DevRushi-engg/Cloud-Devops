# Controller and Agent Architecture

## What it is
Jenkins splits responsibility between two roles.
The controller is the brain. Agents do the actual building.

## The two roles
| Role | What it does |
|------|-------------|
| Controller | Main Jenkins server — schedules jobs, hosts the dashboard |
| Agent | Separate machine that actually runs your builds |

## How they connect
```
CONTROLLER
(schedules jobs, hosts the dashboard)
    │
    ├── Agent 1 (runs builds)
    ├── Agent 2 (runs builds)
    └── Agent 3 (runs builds)
```

## Key Points
- A small setup runs everything on the controller alone — fine for learning
- Bigger teams add agents so builds do not compete for resources
- The controller assigns work — agents do the actual building in parallel
- More agents means more builds can run simultaneously
- Older documentation calls these "master" and "slave" — controller and agent
  is the current terminology
- This is Jenkins' version of GitHub Actions' parallel runners

## Nodes and Executors
| Term | What it is |
|------|-----------|
| Node | Any machine (controller or agent) that can run builds |
| Executor | A slot on a node that runs exactly one build at a time |

More executors = more builds can run in parallel on that node.
Manage Jenkins → Nodes shows every node and its executor count.

## When I use this
Understanding this architecture explains why builds sometimes queue,
and when to add more agents to speed up a busy pipeline.
