# 🛠 Day 5 – Runbook Notes on Troubleshooting

---

# 🔹 System Information Verification

## 1️⃣ Command: `uname -a`

**Observation:**  
System is running an AWS-optimized Ubuntu Linux kernel (6.14.0) on x86_64 architecture.

---

## 2️⃣ Command: `lsb_release -a`

**Observation:**  
System is running Ubuntu 24.04 LTS (noble), confirming a stable LTS environment.

---

# 🔹 Filesystem Validation

## 3️⃣ Command:
```
mkdir /tmp/runbook-demo
```

**Observation:**  
Able to create directory under `/tmp`, confirming filesystem is writable and responsive.

---

## 4️⃣ Command:
```
cp /etc/hosts /tmp/runbook-demo && ls -l /tmp/runbook-demo
```

**Observation:**  
Successfully copied file and verified permissions, confirming normal filesystem read/write operations.

---

# 🔹 Memory Health Check

## 5️⃣ Command:
```
free -h
```

**Observation:**  
System has sufficient available memory (~500MB) with no swap usage, indicating no memory pressure.

---

# 🔹 Process Analysis

## 6️⃣ Command:
```
pidof cron
```

**Observation:**  
Identified cron service process with PID 577 for targeted resource analysis.

---

## 7️⃣ Command:
```
ps -o pid,pcpu,pmem,comm -p 577
```

**Observation:**  
Cron process is consuming negligible CPU and memory, indicating no resource pressure from the service.

---

# 🔹 Disk Space Monitoring

## 8️⃣ Command:
```
df -h
```

**Observation:**  
All filesystems have sufficient free space.  
Root filesystem usage is approximately 48%, ruling out disk space issues.

---

## 9️⃣ Command:
```
du -sh /var/log
```

**Observation:**  
`/var/log` uses approximately 144MB of disk space.  
No excessive log growth observed.  
Permission warnings are expected for protected directories.

---

# 🔹 Network & Port Verification

## 🔟 Command:
```
ss -tulpn
```

**Observation:**  
Expected services like:
- SSH (Port 22)
- HTTP (Port 80)

are listening. No abnormal open ports detected.

---

# 🔹 Application Health Check

## 1️⃣1️⃣ Command:
```
curl -I http://localhost
```

**Observation:**  
Local HTTP service (nginx) responds with `200 OK`, confirming application and network health.

---

# 🔹 Service Log Monitoring

## 1️⃣2️⃣ Command:
```
journalctl -u cron -n 50
```

**Observation:**  
Cron logs show regular job execution and normal service restarts with no recent errors.

---

## 1️⃣3️⃣ Command:
```
tail -n 50 /var/log/nginx/error.log
```

**Observation:**  
No recent errors found in nginx error log, indicating stable application behavior.

---

# 🚨 If the Issue Worsens

1. Restart the affected service and immediately monitor:
   - CPU usage
   - Memory usage
   - Logs after restart

2. Increase log verbosity (if supported) and capture logs during the issue window.

3. Collect deeper diagnostics:
   - `strace`
   - `vmstat`
   - `iostat`

   Escalate with proper evidence.

---

# ✅ Summary

This runbook validates:

- OS and kernel details  
- Filesystem health  
- Memory availability  
- Process resource usage  
- Disk space utilization  
- Network listening ports  
- Application responsiveness  
- Service logs  

A structured troubleshooting approach ensures faster root cause identification and minimal downtime.

---
