# 👥 Day 09 – Linux User & Group Management Challenge

---

## 👤 Users & Groups Created

### 🔹 Users
- tokyo  
- berlin  
- professor  
- nairobi  

### 🔹 Groups
- developers  
- admins  
- project-team  

---

## 🔗 Group Assignments

- **developers** → tokyo, berlin  
- **admins** → berlin, professor  
- **project-team** → nairobi, tokyo  

---

## 📁 Directories Created

### 🔹 `/opt/dev-project`
- Permission: `775`
- Owner: `root`
- Group: `developers`

### 🔹 `/opt/team-workspace`
- Permission: `775`
- Owner: `root`
- Group: `project-team`

---

## 🛠 Commands Used

### 🔹 User Creation
```
sudo useradd -m tokyo
sudo useradd -m berlin
sudo useradd -m professor
sudo useradd -m nairobi
```

Verification:
```
tail -f /etc/passwd
tail -n 3 /etc/passwd
```

---

### 🔹 Group Creation
```
sudo groupadd developers
sudo groupadd admins
sudo groupadd project-team
```

Verification:
```
tail -f /etc/group
tail -n 3 /etc/group
```

---

### 🔹 Assign Users to Groups
```
sudo usermod -aG developers tokyo
sudo usermod -aG developers berlin
sudo usermod -aG admins berlin
sudo usermod -aG admins professor
sudo usermod -aG project-team nairobi
sudo usermod -aG project-team tokyo
```

---

### 🔹 Create & Configure dev-project Directory
```
sudo mkdir -p /opt/dev-project
cd ../opt/
ls -l
sudo chown :developers dev-project/
ls -l
sudo chmod 775 dev-project
ls -l
```

---

### 🔹 Set User Passwords
```
sudo passwd tokyo
sudo passwd berlin
sudo passwd professor
sudo passwd nairobi
```

---

### 🔹 Test Access (dev-project)
```
su berlin
ls
touch new-file.txt
ls -l

su tokyo
touch tokyo-new-file.txt
ls -l
```

---

### 🔹 Create & Configure team-workspace Directory
```
sudo mkdir -p /opt/team-workspace
cd /opt/
ls
sudo chown :project-team team-workspace
sudo chmod 775 team-workspace/
ls -l
```

---

### 🔹 Test Access (team-workspace)
```
su nairobi
cd team-workspace/
touch nairobi-text-file.txt
ls -l
```

---

## 📚 What I Learned

1. Adding users in Linux  
2. Creating groups  
3. Assigning users to groups  
4. Managing directory ownership and permissions  
5. Validating group-based access control  
6. Writing files in shared directories using proper permissions  

---

🚀 **Day 09 – Challenge Completed Successfully**
