# 📂 Day 10 – File Permissions and File Operations

---

# 🎯 Objective

Understand file creation, reading files, Linux file permissions, modifying permissions, and testing access control.

---

# 🔹 TASK 1 – Create Files

### Step 1: Create Working Directory

```
mkdir day10
cd day10
```

---

### Step 2: Create Files

```
touch devops.txt
echo "This is a DevOps hands on practice notes Day 10 challenge" > notes.txt
vi script.sh
```

Inside `script.sh`:

```
echo "Hello DevOps"
```

---

### Step 3: Verify Files

```
ls
```

Files created:
- devops.txt
- notes.txt
- script.sh

---

# 🔹 TASK 2 – Read Files

### Read notes.txt

```
cat notes.txt
```

---

### View First 5 Lines of /etc/passwd

```
head -n 5 /etc/passwd
```

---

### View Last 5 Lines of /etc/passwd

```
tail -n 5 /etc/passwd
```

---

# 🔹 TASK 3 – Understand Permissions

### Check File Permissions

```
ls -l
```

Example Output:

```
-rw-rw-r-- 1 ubuntu ubuntu   0 devops.txt
-rw-rw-r-- 1 ubuntu ubuntu  58 notes.txt
-rw-rw-r-- 1 ubuntu ubuntu  13 script.sh
```

### Permission Breakdown

Format:
```
-rwxrwxrwx
```

- First character → File type (`-` = file, `d` = directory)
- First 3 → Owner permissions
- Next 3 → Group permissions
- Last 3 → Others permissions

r = read  
w = write  
x = execute  

---

# 🔹 TASK 4 – Modify Permissions

### Make script executable

```
chmod +x script.sh
ls -l
```

---

### Modify devops.txt permissions

```
chmod u-w devops.txt
ls -l
```

---

### Create a directory

```
mkdir project
```

---

### Change directory permissions

```
chmod 755 project
ls -l
```

---

### Run the Script

```
./script.sh
```

Output:
```
Hello DevOps
```

---

# 🔹 TASK 5 – Test Permissions

### Try writing to devops.txt (after removing write permission)

```
echo "Testing write permission" > devops.txt
```

Result:
```
Permission denied
```

---

### Try executing notes.txt

```
./notes.txt
```

Result:
```
Permission denied
```

---

# ✅ Key Learning Summary

- Created files and directories
- Read system and custom files
- Understood Linux permission structure
- Modified permissions using `chmod`
- Executed scripts
- Tested write and execute restrictions
- Observed real permission-denied behavior

---

🚀 **Day 10 – File Permissions and File Operations Completed**
