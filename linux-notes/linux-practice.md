# 🐧 Linux Practice - Process and Services

---

## 🔹 Process Monitoring Commands

### 1️⃣ Command: `ps -ef | head`

**Observation:**  
PID 1 is `systemd`, which is the parent of all user-space processes.

---

### 2️⃣ Command: `top`

**Observation:**  
- System load average is `0.00`
- CPU is `100% idle`
- No high CPU-consuming processes were observed.

This indicates the system is healthy and under minimal load.

---

### 3️⃣ Command: `pgrep sshd`

**Observation:**  
Searches for running processes and returns their PID(s) (Process IDs).

Useful for quickly identifying specific running services like `sshd`.

---

# 🔹 Service Management Using systemd

### 4️⃣ Command:
```
systemctl list-units --type=service --state=running | head
```

**Observation:**  
Identified active systemd services such as:

- cron
- ssh
- docker
- containerd

These services are currently running on the system.

---

### 5️⃣ Command:
```
systemctl status cron
```

**Observation:**  
- `cron` service is **enabled**
- `cron` service is **running**
- Recent logs show hourly cron jobs executing successfully

This confirms the cron scheduler is functioning properly.

---

### 6️⃣ Command:
```
journalctl -u cron
```

**Observation:**  
Cron logs show regular execution of scheduled jobs with no errors.

This helps in verifying cron job execution history.

---

# 🔹 Log Monitoring & Troubleshooting

### 7️⃣ Command:
```
tail -n 20 /var/log/syslog
```

**Observation:**  
- System logs show normal cron and sysstat activity
- Noticed `amazon-ssm-agent` errors due to missing EC2 IAM role configuration

This indicates:
- System services are mostly healthy
- IAM role configuration needs to be fixed for Amazon SSM Agent

---

# 🔹 Restarting Services

### 8️⃣ Command:
```
systemctl restart cron
```

**Observation:**  
- Cron service restarted successfully
- Service is running with a new PID

This confirms:
- Service restart was successful
- systemd reassigned a new process ID

---

# ✅ Key Learnings

- `systemd` (PID 1) manages all user-space processes.
- `ps`, `top`, and `pgrep` help in process monitoring.
- `systemctl` is used for service management.
- `journalctl` helps in log analysis.
- `tail` is useful for real-time log troubleshooting.
- Services can be restarted safely using `systemctl restart`.

---

🚀 **Day 04 Linux Practice Completed**
