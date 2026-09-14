# Secrets — Passing Tokens and Keys Safely

## What it does
Stores sensitive values like API tokens, passwords, and SSH keys
encrypted in GitHub. Injects them into workflows without
exposing them in YAML or logs.

## Adding a secret on GitHub
```
1. Go to your repo on GitHub
2. Settings → Secrets and variables → Actions
3. Click "New repository secret"
4. Name it in ALL_CAPS: DEPLOY_TOKEN
5. Paste the value → click Add secret
6. Once saved, GitHub never shows the value again
```

## Using a secret in a workflow
```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Deploy with token
        env:
          TOKEN: ${{ secrets.DEPLOY_TOKEN }}
        run: |
          echo "Token exists: ${#TOKEN} characters"
          # use $TOKEN in your deploy command here
          # NEVER: echo "$TOKEN"
```

## Types of secrets
```yaml
# repository secret
${{ secrets.MY_SECRET }}

# organization secret (shared across repos)
${{ secrets.ORG_SECRET }}

# environment secret (tied to an environment like production)
${{ secrets.PROD_SECRET }}
```

## Safe ways to verify a secret is set
```yaml
- name: Verify secret is present
  run: |
    if [ -z "$TOKEN" ]; then
      echo "ERROR: TOKEN is not set"
      exit 1
    fi
    echo "Token is set (${#TOKEN} chars)"
  env:
    TOKEN: ${{ secrets.DEPLOY_TOKEN }}
```

## ⚠️ Critical Rules
- Never write a secret value directly in the YAML file
- Never `echo "$SECRET"` — print its length `${#SECRET}` instead
- A secret committed to YAML is leaked to the world — rotate it immediately
- GitHub automatically masks secret values in logs as `***`
- Even if masked, never echo secrets — masking can be bypassed

## Key Points
- Secrets are write-only — GitHub never shows the value again after saving
- Reference with `${{ secrets.NAME }}` — name must match exactly
- Available as env vars in steps via the `env:` block
- Organization secrets can be shared across multiple repos
- `GITHUB_TOKEN` is a built-in secret available in every workflow automatically

## When I use this
Deploying to cloud providers (AWS, GCP, Azure), calling external
APIs that need authentication, pushing to package registries.
