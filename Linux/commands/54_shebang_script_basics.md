# Shell Script Basics — Shebang, Creating and Running Scripts

## What it does
A shell script is a text file containing commands that run in sequence.
The shebang line tells Linux which program should run the file.

## Anatomy of a script
```bash
#!/bin/bash
# This is a comment
echo "Hello from a script"
```

## Creating and running
```bash
# create the script
nano hello.sh

# make it executable
chmod +x hello.sh

# run it
./hello.sh

# run without chmod +x
bash hello.sh
```

## My Terminal Output
```bash
rushi@rushi:~$ nano hello.sh
# wrote #!/bin/bash and echo "Hello from a script"

rushi@rushi:~$ chmod +x hello.sh
rushi@rushi:~$ ./hello.sh
Hello from a script

rushi@rushi:~$ bash hello.sh
Hello from a script
```

## Key Points
- Line 1 must be `#!/bin/bash` — called the shebang
- `./hello.sh` runs it from the current folder — the `./` is required
- `bash hello.sh` works even without `chmod +x`
- Name scripts with `.sh` by convention
- A script is just a saved list of the commands you already know
- Always test scripts manually before scheduling with cron

## When I use this
Any time I find myself typing the same sequence of commands more
than twice — time to write a script.

