# Installing and Starting Jenkins

## What it does
Installs Jenkins from the official repository, starts the service,
and enables it to start automatically on every boot.

## Syntax
```bash
# install Jenkins
sudo apt install -y jenkins

# start Jenkins now
sudo systemctl start jenkins

# enable it to start on every boot
sudo systemctl enable jenkins

# confirm it is running
sudo systemctl status jenkins
```

## My Terminal Output
```bash
rushi@rushi:~$ sudo apt install -y jenkins
Reading package lists... Done
Setting up jenkins (2.462.1) ...

rushi@rushi:~$ sudo systemctl start jenkins
rushi@rushi:~$ sudo systemctl enable jenkins
Created symlink /etc/systemd/system/multi-user.target.wants/jenkins.service

rushi@rushi:~$ sudo systemctl status jenkins
● jenkins.service - Jenkins Continuous Integration Server
     Loaded: loaded (/lib/systemd/system/jenkins.service; enabled)
     Active: active (running) since Mon 2026-08-11 10:00:00 IST
```

## If running on a cloud server or behind a firewall
```bash
# open port 8080 so the web UI is accessible
sudo ufw allow 8080
sudo ufw status
```

## Useful Jenkins service commands
```bash
sudo systemctl start jenkins      # start
sudo systemctl stop jenkins       # stop
sudo systemctl restart jenkins    # restart after config changes
sudo systemctl status jenkins     # check if running
sudo systemctl enable jenkins     # start on boot
sudo systemctl disable jenkins    # do not start on boot
```

## Key Points
- Jenkins runs on port 8080 by default
- `active (running)` in green means it started successfully
- Press `q` to exit the status view
- Jenkins is managed by systemd — same commands as nginx, ssh, etc
- Logs are available with `journalctl -u jenkins -f`

## When I use this
Initial setup and whenever Jenkins needs to be restarted after
plugin installation or configuration changes.
