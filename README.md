# Linux Fundamentals for DevOps

This repository contains my notes, commands, and lab exercises while learning **Linux for DevOps and Cloud Engineering**.

Linux is the backbone of most modern cloud infrastructure, servers, and DevOps pipelines. This repository documents the core Linux concepts required for system administration and DevOps roles.

---

# 1. What is Linux

Linux is a **free and open-source operating system kernel** created by **Linus Torvalds**.

### Features
- Open source
- Multi-user
- Multitasking
- Secure permission model
- Portable (runs on servers, desktops, embedded systems)
- Highly stable and scalable

---

# 2. Linux Distributions

A **Linux distribution (distro)** is a complete operating system built using the Linux kernel.

### Popular Distributions

#### Desktop
- Ubuntu
- Linux Mint
- Zorin OS

#### Enterprise / Server
- Red Hat Enterprise Linux (RHEL)
- CentOS
- Debian
- SUSE Linux Enterprise Server

#### Security
- Kali Linux
- Parrot OS

---

# 3. Linux File System

Linux follows a **hierarchical directory structure** starting from the root directory `/`.

### Important Directories

| Directory | Description |
|---|---|
| / | Root directory |
| /bin | Essential user binaries |
| /sbin | System binaries |
| /etc | Configuration files |
| /home | User home directories |
| /root | Root user home |
| /var | Logs and variable data |
| /tmp | Temporary files |
| /usr | User programs and libraries |
| /boot | Boot loader files |
| /dev | Device files |
| /proc | Process information |
| /sys | Kernel and hardware information |

---

# 4. Linux File System Types

| File System | Description |
|---|---|
| ext2 | Old filesystem without journaling |
| ext3 | ext2 with journaling |
| ext4 | Default filesystem for most Linux systems |

---

# 5. System Users vs Manual Users

### System Users
- Created by the system
- Used for running services
- UID range: **1 – 999**

Examples:
- mysql
- nginx
- apache

### Manual Users
- Created by administrators
- Used for human login

UID range: **1000+**

---

# 6. User Management

### Create User
```bash
useradd username
```

### Create User with Home Directory
```bash
useradd -m username
```

### Set Password
```bash
passwd username
```

### Delete User
```bash
userdel username
```

### Delete User with Home Directory
```bash
userdel -r username
```

### Check Current User
```bash
whoami
```

### Check User ID
```bash
id
```

---

# 7. Group Management

### Create Group
```bash
groupadd groupname
```

### Delete Group
```bash
groupdel groupname
```

### Modify Group Name
```bash
groupmod -n newname oldname
```

### Add User to Group
```bash
usermod -aG groupname username
```

---

# 8. File Permissions

Linux uses **three permission types**

| Permission | Symbol | Value |
|---|---|---|
| Read | r | 4 |
| Write | w | 2 |
| Execute | x | 1 |

### Entities

| Entity | Meaning |
|---|---|
| u | User (owner) |
| g | Group |
| o | Others |
| a | All |

---

# 9. Viewing Permissions

```bash
ls -l
```

Example

```
-rwxr-xr-x
```

---

# 10. Changing Permissions

### Symbolic Mode

Add permission

```bash
chmod u+x file
```

Remove permission

```bash
chmod g-w file
```

Set permission

```bash
chmod u=rwx file
```

---

### Numeric Mode

Example

```bash
chmod 755 file
```

Explanation

```
7 = rwx
5 = r-x
5 = r-x
```

---

# 11. Ownership Management

Change owner

```bash
chown user file
```

Change group

```bash
chgrp group file
```

Change both

```bash
chown user:group file
```

---

# 12. Package Management

Package managers install and manage software.

### Debian / Ubuntu

```bash
apt update
apt install nginx
apt remove nginx
```

Uses:
- apt
- dpkg

---

### RHEL / CentOS / Fedora

```bash
yum install nginx
dnf install nginx
```

---

### Arch Linux

```bash
pacman -S nginx
```

---

# 13. Basic Linux Commands

### Copy Files

```bash
cp source destination
```

### Move / Rename

```bash
mv source destination
```

### Find Files

```bash
find /path -name filename
```

### Locate Files

```bash
locate filename
```

---

# 14. Pipes and Filters

Pipe `|` passes output of one command to another.

Example

```bash
cat file.txt | grep hello
```

---

# 15. Archive and Compression

### Create Archive

```bash
tar -cvf archive.tar folder
```

### Extract

```bash
tar -xvf archive.tar
```

### List Contents

```bash
tar -tvf archive.tar
```

---

# 16. Process Management

### View Processes

```bash
ps
ps aux
```

### Process ID

Every process has a **PID**

---

# 17. Signals

Signals are messages sent to processes.

| Signal | Number | Description |
|---|---|---|
| SIGTERM | 15 | Graceful termination |
| SIGKILL | 9 | Force kill |
| SIGINT | 2 | Interrupt (Ctrl+C) |
| SIGSTOP | 19 | Stop process |

Kill process

```bash
kill PID
```

Force kill

```bash
kill -9 PID
```

Kill by name

```bash
pkill processname
```

---

# 18. Process Priority

Priority range

```
-20 (highest)
19 (lowest)
```

Run process with priority

```bash
nice -n 10 command
```

Change priority

```bash
renice -n -5 -p PID
```

---

# 19. Monitoring

### Logs

System logs are stored in

```
/var/log
```

Examples

```
/var/log/syslog
/var/log/messages
```

### journalctl

View systemd logs

```bash
journalctl
journalctl -xe
```

---

### Metrics Monitoring Tools

Common tools

- top
- htop
- vmstat
- iostat
- free

Example

```bash
top
```

---

# 20. Hard Link vs Soft Link

### Hard Link

```bash
ln file hardlink
```

Characteristics

- Same inode
- Cannot cross filesystems
- Works even if original file deleted

---

### Soft Link (Symbolic Link)

```bash
ln -s file softlink
```

Characteristics

- Pointer to original file
- Can cross filesystem
- Breaks if original deleted

---

# 21. Cron Jobs (Task Scheduling)

Cron is used to schedule tasks automatically.

### Edit Cron

```bash
crontab -e
```

### Format

```
* * * * * command
```

Fields

```
minute hour day month weekday command
```

Example

Run script every day at 2AM

```bash
0 2 * * * /home/user/backup.sh
```

---

# 22. Shell

A shell is a **command interpreter** between user and kernel.

### Types of Shells

- sh
- bash
- ksh
- csh
- zsh
- fish
- dash

Most common: **Bash**

---

# 23. Shell Scripting Basics

### Shebang

Defines interpreter

```bash
#!/bin/bash
```

Example script

```bash
#!/bin/bash

echo "Hello DevOps"
```

### Run Script

```bash
bash script.sh
```

or

```bash
./script.sh
```

---

# 24. Lab Exercises

## Lab 1 — User Management

Create user

```bash
sudo useradd devops
sudo passwd devops
```

Verify

```bash
id devops
```

Delete user

```bash
sudo userdel -r devops
```

---

## Lab 2 — Permissions

Create file

```bash
touch test.txt
```

Change permissions

```bash
chmod 755 test.txt
```

Check

```bash
ls -l
```

---

## Lab 3 — Soft and Hard Links

Create file

```bash
touch file1
```

Hard link

```bash
ln file1 hardlink
```

Soft link

```bash
ln -s file1 softlink
```

---

## Lab 4 — Cron Job

Open cron

```bash
crontab -e
```

Add job

```
*/5 * * * * echo "Hello DevOps" >> test.log
```

---

## Lab 5 — Process Management

Run process

```bash
sleep 100
```

Find PID

```bash
ps aux
```

Kill process

```bash
kill PID
```

---

# 25. Why Linux is Important for DevOps

Linux is used in

- Cloud servers
- Containers (Docker)
- Kubernetes nodes
- CI/CD pipelines
- Infrastructure automation

Understanding Linux is **essential for DevOps Engineers**.

---

# Author

Mohammed Rinas  
DevOps & Cloud Learner
