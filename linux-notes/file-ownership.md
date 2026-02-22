# 📂 Day 11 – File Ownership Challenge (chown and chgrp)

---

# 🎯 Objective

Understand and practice:

- File ownership
- Group ownership
- `chown` command
- `chgrp` command
- Recursive ownership changes

---

# 🔹 TASK 1 – Understanding Ownership

### Check Ownership

```
ls -l
```

Observation:

- Column 3 → Owner
- Column 4 → Group
- In the initial state, both owner and group were `ubuntu`

---

## 🔍 Difference Between Owner and Group (Linux)

### 🔹 Owner
The owner is a **single user** who owns the file or directory.  
Owner permissions determine what that specific user can do (read, write, execute).

### 🔹 Group
The group represents a **collection of users**.  
Any user belonging to that group can access the file or directory according to group permissions.

---

# 🔹 TASK 2 – Basic `chown` Operation

### Create File

```
sudo touch devops-file.txt
ls -l
```

Initially:
- Owner: root
- Group: root

---

### Attempt Without sudo (Fails)

```
chown tokyo devops-file.txt
```

Result:
```
Operation not permitted
```

---

### Change Owner with sudo

```
sudo chown tokyo devops-file.txt
```

---

### Change Owner Again

```
sudo chown berlin devops-file.txt
```

Owner successfully changed.

---

# 🔹 TASK 3 – Basic `chgrp` Operations

### Create File

```
sudo touch team-notes.txt
```

---

### Create Group

```
sudo groupadd hiest-team
```

---

### Change Group Ownership

```
sudo chgrp hiest-team team-notes.txt
```

Group ownership updated successfully.

---

# 🔹 TASK 4 – Combined Ownership and Group Change

### Create File

```
sudo touch project-config.yaml
```

---

### Change Owner and Group Together

```
sudo chown professor:hiest-team project-config.yaml
```

Both owner and group updated in one command.

---

### Attempt Without sudo (Fails)

```
chown berlin:hiest-team app-logs
```

Result:
```
Operation not permitted
```

---

### Fix with sudo

```
sudo chown berlin:hiest-team app-logs
```

Ownership updated successfully.

---

# 🔹 TASK 5 – Recursive Operations

### Create Project Structure

```
sudo mkdir -p hiest-project/vault
sudo mkdir -p hiest-project/plans
sudo touch hiest-project/vault/gold.txt
sudo touch hiest-project/plans/strategy.conf
```

---

### Verify Structure

```
ls -lR hiest-project/
```

---

### Create New Group

```
sudo groupadd planners
```

---

### Apply Recursive Ownership

```
sudo chown -R professor:planners hiest-project/
```

All files and subdirectories updated recursively.

---

# 🔹 TASK 6 – Practice Challenge

### Create Groups

```
sudo groupadd vault-team
sudo groupadd tech-team
```

---

### Create Directory

```
sudo mkdir bank-heist
```

---

### Create Files

```
sudo touch bank-heist/access-codes.txt
sudo touch bank-heist/blueprints.pdf
sudo touch bank-heist/escape-plan.txt
```

---

### Assign Ownership

```
sudo chown tokyo:vault-team access-codes.txt
sudo chown berlin:tech-team blueprints.pdf
sudo chown nairobi:vault-team escape-plan.txt
```

---

# ✅ Key Learning Summary

- Understood difference between owner and group
- Used `chown` to change file ownership
- Used `chgrp` to change group ownership
- Combined owner and group changes
- Applied recursive ownership changes
- Practiced real-world multi-user permission management

---

🚀 **Day 11 – File Ownership Challenge Completed**
