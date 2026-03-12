# Permission Management

Linux uses permissions to control file access.

---

# Permission Types

| Permission | Symbol |
|------|------|
| Read | r |
| Write | w |
| Execute | x |

---

# Entities

| Entity | Meaning |
|------|------|
| u | Owner |
| g | Group |
| o | Others |

---

# View Permissions

```
ls -l
```

Example

```
-rwxr-xr-x
```

---

# Change Permissions

Symbolic method

```
chmod u+x file
```

Numeric method

```
chmod 755 file
```

---

# Lab Exercise

Create file

```
touch test.txt
```

Change permission

```
chmod 755 test.txt
```

Check permission

```
ls -l
```
