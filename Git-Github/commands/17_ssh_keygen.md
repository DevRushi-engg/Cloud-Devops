# ssh-keygen — Generate SSH Key Pair for GitHub

## What it does
Creates two files: a private key and a public key.
The public key goes to GitHub. The private key stays on your machine.
Set it up once and never type a password for GitHub again.

## Syntax
```bash
ssh-keygen -t ed25519 -C "you@example.com"
# press Enter 3 times to accept all defaults

# view your public key
cat ~/.ssh/id_ed25519.pub

# test the connection after adding to GitHub
ssh -T git@github.com
```

## My Terminal Output
```bash
rushi@rushi:~$ ssh-keygen -t ed25519 -C "rushi@example.com"
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/rushi/.ssh/id_ed25519):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /home/rushi/.ssh/id_ed25519
Your public key has been saved in /home/rushi/.ssh/id_ed25519.pub

rushi@rushi:~$ cat ~/.ssh/id_ed25519.pub
ssh-ed25519 AAAAC3Nza... rushi@example.com

rushi@rushi:~$ ssh -T git@github.com
Hi DevRushi-engg! You've successfully authenticated.
```

## Files created
| File | What it is |
|------|-----------|
| `~/.ssh/id_ed25519` | Private key — NEVER share this |
| `~/.ssh/id_ed25519.pub` | Public key — safe to give GitHub |

## Adding to GitHub
1. Copy output of `cat ~/.ssh/id_ed25519.pub`
2. Go to GitHub → Settings → SSH and GPG keys → New SSH key
3. Paste it, give it a title, save
4. Test with `ssh -T git@github.com`

## Key Points
- `ed25519` is the modern secure key type — use this over `rsa`
- The passphrase is optional but adds an extra layer of security
- Never share, commit, or paste your private key anywhere
- Only the `.pub` file goes to GitHub
- One key pair can be used for multiple GitHub repos

## When I use this
Once per machine — after setting up a new laptop, VM, or
cloud instance that needs to push to GitHub.o

