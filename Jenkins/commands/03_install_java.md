# Installing Java — Jenkins Prerequisite

## What it does
Jenkins is a Java application so a Java runtime must be installed
before Jenkins itself. OpenJDK 21 is the current recommended version.

## Syntax
```bash
# update package list
sudo apt update

# install Java runtime and fontconfig
sudo apt install -y fontconfig openjdk-21-jre

# confirm it installed correctly
java -version
```

## My Terminal Output
```bash
rushi@rushi:~$ sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu jammy InRelease
Reading package lists... Done

rushi@rushi:~$ sudo apt install -y fontconfig openjdk-21-jre
Reading package lists... Done
Setting up openjdk-21-jre (21.0.3+9-1~22.04.1) ...
Setting up fontconfig (2.13.1-4.2ubuntu5) ...

rushi@rushi:~$ java -version
openjdk version "21.0.3" 2026-04-15
OpenJDK Runtime Environment (build 21.0.3+9-Ubuntu)
```

## Key Points
- Jenkins will not start without a Java runtime
- OpenJDK 21 is the current recommended version for Jenkins
- `fontconfig` is needed so Jenkins renders its web pages correctly
- Always run `java -version` to confirm before continuing to Jenkins install
- Install Java first, then add the Jenkins repository

## When I use this
First step on any new machine where Jenkins needs to be installed.
