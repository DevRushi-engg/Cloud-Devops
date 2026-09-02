# ssh & scp — Remote Login and Secure File Copy

## What it does
`ssh` opens a secure encrypted shell session on a remote machine.
`scp` copies files securely between machines over SSH.
The backbone of managing remote servers.

## Syntax
```bash
ssh user@192.168.1.10           # login with password
ssh -i key.pem user@host        # login with a private key
ssh user@host "ls /var/log"     # run one command remotely

scp file.txt user@host:/home/user/        # copy TO remote
scp user@host:/home/user/file.txt .       # copy FROM remote
scp -r folder/ user@host:/home/user/      # copy a folder
```

## My Terminal Output
```bash
rushi@rushi:~$ ssh rushi@192.168.1.10
The authenticity of host '192.168.1.10' can't be established.
Are you sure you want to continue connecting? yes
rushi@192.168.1.10's password:
Welcome to Ubuntu 22.04

rushi@192.168.1.10:~$ whoami
rushi
rushi@192.168.1.10:~$ exit

rushi@rushi:~$ scp notes.txt rushi@192.168.1.10:/home/rushi/
notes.txt    100%  512   1.2MB/s   00:00
```

## Key Points
- `user@host` tells SSH who you are and where to connect
- `-i key.pem` uses a private key instead of a password — standard in cloud
- On first connection SSH asks to confirm the host fingerprint — type `yes`
- `exit` or `Ctrl+D` to end the SSH session
- `scp -r` is needed to copy whole directories
- Port 22 must be open on the remote machine for SSH to work

## When I use this
Logging into cloud VMs (AWS EC2, GCP, Azure), copying config files
and scripts to remote servers, running quick remote commands.
