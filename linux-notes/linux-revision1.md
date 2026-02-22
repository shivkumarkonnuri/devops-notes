# 🌿 Day 12 – Breather & Revision (Days 01–11)

---

# 🎯 Reflection Overview

Day 12 was focused on revision and self-evaluation of progress from Days 01 to 11.  
The goal was to reinforce learning, validate understanding, and identify improvement areas.

---

## 📅 Day 1 – Learning Plan Review

After revisiting Day 01:

- My learning plan is still aligned with my goals.
- The step-by-step and hands-on approach from Days 1–11 has helped me build a strong foundation.
- No changes are required to the plan at this stage.

---

## 🔍 Day 4–5 – Service Health Check

I verified service status and logs for:

- Nginx
- Docker

### Commands Used:

```
systemctl status nginx
systemctl status docker
journalctl -u nginx
journalctl -u docker
```

### Observation:

- Both services were active and running.
- Services were enabled at boot.
- No errors were found in logs.

---

## 📂 Day 6–11 – File Operations & Permissions

I practiced file and permission-related commands extensively and have also used them in prior work experience.

### Commands I’m Comfortable With:

- `chmod`
- `chown`
- `ls -l`

### Current Learning Focus:

Understanding:

- When to assign full permissions (`777`)
- When to assign limited permissions (`755`, `644`, etc.)
- How to apply secure-by-default practices while setting up new servers

I usually know what to fix when errors occur, but now I want to be more intentional and security-conscious from the beginning.

---

# 📘 Cheat Sheet Refresh (Day 03)

During revision, I reviewed my Linux cheat sheet and identified the commands I would immediately use during an incident.

These commands provide:

- Quick visibility into service health
- Log insights
- Process confirmation
- Permission validation

---

## 🚀 Top 5 Commands I’d Reach for First

### 1️⃣ `systemctl status <service>`

Quickly checks:
- Whether a service is running, failed, or inactive
- Recent error messages

---

### 2️⃣ `journalctl -u <service>`

Used to:
- Analyze service logs
- Understand root causes of failures
- Trace unexpected behavior

---

### 3️⃣ `ps -ef | grep <service>`

Used to:
- Confirm whether a process is running
- Identify the PID

---

### 4️⃣ `systemctl is-enabled <service>`

Used to:
- Verify whether the service starts automatically after reboot

---

### 5️⃣ `ls -l`

Used to:
- Check file permissions
- Verify file ownership
- Troubleshoot access and execution issues

---

# 🧠 Key Takeaway

These commands together help me:

- Assess service health
- Trace failures using logs
- Confirm process execution
- Validate file permissions

These are the **first steps I take during real production incidents**.

---

# 👥 User / Group Sanity Check (Days 09 & 11)

During revision, I:

- Created users and groups
- Assigned users to groups
- Created files and directories with specific owners and groups
- Tested access control

### Observations:

- A user who was not the owner but part of the assigned group could access files based on group permissions.
- A user who was neither owner nor group member (and had no “others” permissions) could not access the files.

This confirmed proper group-based access control implementation.

---

# ⚡ Which 3 Commands Save Me the Most Time Right Now?

### 1️⃣ `systemctl status <service>`

- Immediate view of service state
- Shows recent error logs inline

---

### 2️⃣ `journalctl -u <service>`

- Helps identify root cause quickly
- Essential for debugging service issues

---

### 3️⃣ `ls -l`

- Instantly verifies ownership and permissions
- Very helpful during execution or access errors

---

# ✅ Final Reflection

Days 01–11 have:

- Strengthened my Linux fundamentals
- Improved troubleshooting confidence
- Reinforced real-world DevOps practices
- Enhanced my ability to diagnose issues quickly

🚀 **Day 12 – Revision & Reflection Completed**
