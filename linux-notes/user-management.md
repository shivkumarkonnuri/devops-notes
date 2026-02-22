# 👥 Day 09 – Linux User & Group Management Challenge

---

# 🎯 Objective

Practice Linux user and group management by:

- Creating users
- Creating groups
- Assigning users to groups
- Managing shared directories
- Setting up a team workspace

---

# 🔹 Task 1 – Create Users

### Commands Used:

```
sudo useradd -m tokyo
sudo useradd -m berlin
sudo useradd -m professor
```

### Verification:

```
tail /etc/passwd
```

Users created:
- tokyo
- berlin
- professor

Each user has:
- Home directory
- Default shell `/bin/sh`

---

# 🔹 Task 2 – Create Groups

### Commands Used:

```
sudo groupadd developers
sudo groupadd admins
```

### Verification:

```
tail -n 10 /etc/group
```

Groups created:
- developers
- admins

---

# 🔹 Task 3 – Assign Users to Groups

### Commands Used:

```
sudo usermod -aG developers tokyo
sudo usermod -aG developers berlin
sudo usermod -aG admins berlin
sudo usermod -aG admins professor
```

### Verification:

```
tail -n 10 /etc/group
```

Group Membership:

- developers → tokyo, berlin  
- admins → berlin, professor  

---

# 🔹 Task 4 – Shared Directory (Developers Team)

### Step 1: Create Shared Directory

```
sudo mkdir -p /opt/dev-project
```

### Step 2: Change Group Ownership

```
sudo chown :developers /opt/dev-project
```

### Step 3: Set Permissions

```
sudo chmod 775 /opt/dev-project
```

### Directory Permission Meaning:

- Owner: Full access
- Group (developers): Read, Write, Execute
- Others: Read, Execute

---

### Testing Access

Switch user:

```
su berlin
cd /opt/dev-project
touch new-file.txt
```

Switch user:

```
su tokyo
cd /opt/dev-project
touch tokyo-new-file.txt
```

Files created successfully → Shared access working correctly.

---

# 🔹 Task 5 – Team Workspace

### Step 1: Create New User

```
sudo useradd -m nairobi
```

### Step 2: Create New Group

```
sudo groupadd project-team
```

### Step 3: Add Users to Group

```
sudo usermod -aG project-team nairobi
sudo usermod -aG project-team tokyo
```

### Step 4: Create Workspace Directory

Initially failed due to permission:

```
mkdir -p /opt/team-workspace
```

Corrected using sudo:

```
sudo mkdir -p /opt/team-workspace
```

### Step 5: Change Ownership & Permissions

```
sudo chown :project-team /opt/team-workspace
sudo chmod 775 /opt/team-workspace
```

---

### Testing Team Workspace

Switch to user:

```
su nairobi
cd /opt/team-workspace
touch nairobi-text-file.txt
```

File created successfully → Workspace configured properly.

---

# ✅ Key Learning Summary

- Created multiple Linux users
- Created and managed groups
- Assigned users to multiple groups
- Managed shared directory permissions
- Used `chown`, `chmod`, `usermod`, `groupadd`
- Validated group-based access control
- Practiced real-world DevOps-style user management

---

🚀 **Day 09 – User & Group Management Challenge Completed**
