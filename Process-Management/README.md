# Process Management

A process is a running instance of a program.

Each process has a **PID**.

---

# Important Commands

| Command | Description |
|------|-------------|
| ps | show running processes |
| top | real-time monitoring |
| kill | terminate process |
| pkill | kill process by name |

Example

```
ps aux
```

---

# Kill Process

```
kill PID
```

Force kill

```
kill -9 PID
```

---

# Lab Exercise

Start process

```
sleep 100
```

Find process

```
ps aux
```

Kill process

```
kill PID
```
