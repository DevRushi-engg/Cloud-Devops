# Build Triggers — When Jenkins Runs a Job Automatically

## What it is
Triggers decide when a job should build automatically.
Without a trigger, you click Build Now every time manually.

## Types of triggers
```
In job configuration → Build Triggers section
```

| Trigger | How it works |
|---------|-------------|
| Build periodically | Runs on a cron schedule — no repo check |
| Poll SCM | Checks the repo on a schedule for new commits |
| GitHub hook trigger | GitHub tells Jenkins instantly when code is pushed |
| Trigger builds remotely | A URL call starts the build |
| Build after other projects | Chains jobs — runs when another job succeeds |

## Poll SCM schedule
```
# under Build Triggers → tick "Poll SCM" → enter:
H/5 * * * *
```

Same five-field cron format as Linux cron:
```
H/5 * * * *
│    │ │ │ └── day of week
│    │ │ └──── month
│    │ └────── day of month
│    └──────── hour
└────────────── minute (H = hashed, spreads load)
```

`H/5` means roughly every 5 minutes.
`H` spreads the exact minute across jobs so many do not poll at once.

## GitHub webhook (instant, preferred)
```
1. In Jenkins job: Build Triggers → tick "GitHub hook trigger for GITScm polling"
2. On GitHub: repo Settings → Webhooks → Add webhook
3. Payload URL: http://your-jenkins-url:8080/github-webhook/
4. Content type: application/json
5. Trigger: Just the push event
6. Click Add webhook
```
GitHub now notifies Jenkins the instant code is pushed — no polling needed.

## Key Points
- Webhooks are instant — polling is simpler to set up but a little slower
- Poll SCM only starts a build if the repo actually changed since last poll
- "Build periodically" runs regardless of whether anything changed
- For local Jenkins without a public URL, Poll SCM is easier than webhooks
- Multiple triggers can be enabled at the same time

## When I use this
Setting up automatic builds so the team does not need to
manually click Build Now after every push.

