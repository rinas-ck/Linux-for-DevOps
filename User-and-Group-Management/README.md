# User and Group Management

Linux supports multiple users and groups.

---

# Create User

```
useradd username
```

Set password

```
passwd username
```

Delete user

```
userdel username
```

---

# Group Commands

Create group

```
groupadd groupname
```

Add user to group

```
usermod -aG groupname username
```

---

# Lab Exercise

Create user

```
sudo useradd devops
```

Set password

```
sudo passwd devops
```

Check user ID

```
id devops
```
