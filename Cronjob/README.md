# ⏰ Cron Jobs in Linux

## What is a Cron Job?

A **cron job** is a scheduled task that runs automatically at a specific time or interval.

Linux uses a background service called **cron daemon (crond)** to run scheduled tasks.

Cron helps automate repetitive tasks like:

- Backups
- Log cleanup
- System updates
- Running scripts

---

# Cron Components

### Cron Daemon
The background service that checks schedules every minute.

### Crontab
The file where cron jobs are stored.

### Cron Expression
Defines when the job should run.

### Command
The script or command executed.

---

# Managing Cron Jobs

### Edit Cron Jobs

```
crontab -e
```

### List Cron Jobs

```
crontab -l
```

### Remove Cron Jobs

```
crontab -r
```

---

# Cron Job Syntax

```
* * * * * command
```

| Field | Meaning |
|------|-------|
| Minute | 0–59 |
| Hour | 0–23 |
| Day | 1–31 |
| Month | 1–12 |
| Weekday | 0–7 |

Example:

```
0 2 * * * backup.sh
```

Runs every day at **2 AM**.

---

# Special Characters

| Symbol | Meaning |
|------|-------|
| * | Every value |
| , | Multiple values |
| - | Range |
| / | Step values |

Example

```
*/5 * * * *
```

Runs every **5 minutes**.

---

# Predefined Cron Jobs

| Macro | Meaning |
|------|-------|
| @reboot | Run on system startup |
| @daily | Run daily |
| @weekly | Run weekly |
| @monthly | Run monthly |

Example

```
@daily /home/user/backup.sh
```

---

# Lab Exercise

### Create a Simple Cron Job

1️⃣ Open cron editor

```
crontab -e
```

2️⃣ Add this line

```
*/1 * * * * echo "Cron Job Running" >> test.log
```

3️⃣ Save the file.

4️⃣ Check the output

```
cat test.log
```

---

# Best Practices

✔ Use absolute paths  
✔ Redirect output to logs  
✔ Test scripts before scheduling  

Example

```
0 2 * * * /home/user/script.sh >> /var/log/script.log 2>&1
```

---

# Troubleshooting

Check cron logs

```
journalctl -u cron
```

or

```
cat /var/log/syslog
```

---

# Summary

Cron is a powerful tool in Linux that helps automate tasks and reduce manual work. It is widely used by **system administrators and DevOps engineers**.
