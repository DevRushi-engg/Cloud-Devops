# Unlocking Jenkins — First Run Setup

## What it does
On first run Jenkins generates a one-time password and displays
an unlock screen. You paste the password to prove you have
server access before setting up your admin account.

## Step by step
```bash
# 1. open a browser and go to
http://localhost:8080

# 2. Jenkins shows the "Unlock Jenkins" screen
# 3. get the initial admin password from the terminal
sudo cat /var/lib/jenkins/secrets/initialAdminPassword

# 4. copy the output and paste it into the browser field
# 5. click Continue
```

## My Terminal Output
```bash
rushi@rushi:~$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword
a1b2c3d4e5f6789012345678901234ab
```

## After unlocking — what comes next
```
1. Customize Jenkins screen appears
   → Click "Install suggested plugins"
   → Wait for all plugins to download and install

2. Create First Admin User
   → Fill in: username, password, full name, email
   → Click "Save and Continue"

3. Instance Configuration
   → Confirm the Jenkins URL (keep the default)
   → Click "Save and Finish"

4. Click "Start using Jenkins"
   → You land on the Jenkins dashboard
```

## Key Points
- The initial password is a one-time setup key — only used this once
- `sudo` is required to read the file — it is owned by the jenkins user
- "Install suggested plugins" installs Git, Pipeline, and other
  commonly needed plugins in one click
- Save your admin username and password somewhere safe
- If the setup page looks frozen, wait — plugin downloads take a minute

## When I use this
Only once — the very first time Jenkins is set up on a new machine.
