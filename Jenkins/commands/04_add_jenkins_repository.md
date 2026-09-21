# Adding the Jenkins Repository — apt Source Setup

## What it does
Jenkins is not included in Ubuntu's default package repositories.
This adds the official Jenkins apt repository so `apt install jenkins`
works correctly.

## Syntax
```bash
# create the keyrings directory if it does not exist
sudo mkdir -p /etc/apt/keyrings

# download the Jenkins signing key
sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key

# add the Jenkins repository to apt sources
echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/" | \
  sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null

# refresh the package list to include Jenkins
sudo apt update
```

## My Terminal Output
```bash
rushi@rushi:~$ sudo mkdir -p /etc/apt/keyrings

rushi@rushi:~$ sudo wget -O /etc/apt/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2026.key
2026-08-11 10:00:01 (1.50 MB/s) - '/etc/apt/keyrings/jenkins-keyring.asc' saved

rushi@rushi:~$ echo "deb [signed-by=/etc/apt/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/" | \
  sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null

rushi@rushi:~$ sudo apt update
Hit:1 https://pkg.jenkins.io/debian-stable binary/ InRelease
Reading package lists... Done
```

## Key Points
- This step only needs to be done once per machine
- The signing key verifies packages actually come from Jenkins
- `/etc/apt/keyrings/` is the modern location for apt signing keys
- `/etc/apt/sources.list.d/jenkins.list` is where the repo source is saved
- After this, Jenkins updates automatically when you run `sudo apt upgrade`

## When I use this
Once per machine, before the first Jenkins installation.
