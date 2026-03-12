# Cron Jobs

Cron is used to schedule tasks automatically.

---

# Edit Cron

```
crontab -e
```

List jobs

```
crontab -l
```

Remove jobs

```
crontab -r
```

---

# Cron Syntax

```
* * * * * command
```

Fields

```
minute hour day month weekday
```

Example

```
0 2 * * * backup.sh
```

Run daily at 2 AM.

---

# Lab Exercise

Open cron

```
crontab -e
```

Add job

```
*/1 * * * * echo "Cron running" >> test.log
```
