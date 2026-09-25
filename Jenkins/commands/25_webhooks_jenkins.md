# Webhooks — Instant Build Triggers from GitHub

## What it does
GitHub sends a notification to Jenkins the instant you push code.
Jenkins starts the build immediately — no polling delay.

## Poll SCM vs Webhook
| | Poll SCM | Webhook |
|-|----------|---------|
| How it works | Jenkins checks repo on a timer | GitHub notifies Jenkins instantly |
| Speed | Delay based on poll interval | Builds start within seconds |
| Network requirement | Jenkins can be private | Jenkins must be reachable from GitHub |
| Use case | Learning and local setups | Real team projects |

## Setting up a GitHub webhook
```
On GitHub:
1. Go to your repo → Settings → Webhooks
2. Click "Add webhook"
3. Payload URL: http://YOUR_JENKINS_URL:8080/github-webhook/
4. Content type: application/json
5. Which events: Just the push event
6. Click "Add webhook"

In Jenkins job:
1. Open the Pipeline job configuration
2. Build Triggers section
3. Tick: "GitHub hook trigger for GITScm polling"
4. Click Save
```

## Testing the webhook
```bash
# push any change to trigger it
echo "# test" >> README.md
git add README.md
git commit -m "test: trigger webhook"
git push
# Jenkins should start building within seconds
```

## If Jenkins is not publicly reachable (local setup)
```bash
# use ngrok to expose localhost temporarily
# install ngrok, then:
ngrok http 8080
# use the https URL ngrok gives you as the webhook payload URL
```

## Key Points
- Jenkins must have a public URL for GitHub to reach it
- The payload URL always ends with `/github-webhook/`
- Without a public URL, Poll SCM is the practical alternative
- Ngrok is useful for local development and testing webhooks
- The GitHub plugin must be installed for webhook triggers to work

## When I use this
Any Jenkins server that is publicly accessible — webhooks make
the pipeline feel instant and reduce unnecessary polling load.
