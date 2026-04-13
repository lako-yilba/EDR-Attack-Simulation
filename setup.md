# 🔧 Lab Setup

## 📌 Overview

This lab was created to simulate real-world attacks and detect them using **Sysmon** and **Wazuh**.

---

## 🧱 Architecture
Kali Linux (Attacker)
↓
Windows (Sysmon + Wazuh Agent)
↓
Ubuntu (Wazuh Server + Dashboard)


---

## 🖥️ Windows Setup (Target Machine)

### 🔹 Sysmon Installation

Sysmon was installed to capture detailed system activity.


### ✅ Verification

- Open Event Viewer  
- Navigate to:


📸 **Sysmon Logs**
![Sysmon Logs](../screenshots/sysmon-logs.png)

---

### 🔹 OpenSSH Setup

Since Windows Home does not support RDP, SSH was used.

### 🔹 Test User Creation

A test user was created for brute force simulation.

## 🛡️ Wazuh Setup (SIEM)

### 🔹 Installation

Wazuh was installed on Ubuntu using:

``` bash
curl -sO https://packages.wazuh.com/4.x/wazuh-install.sh

sudo bash wazuh-install.sh -a

```


---

### ⚠️ Issue Faced

During installation, the setup failed due to low disk space.

### 🔧 Fix

- Increased virtual disk size  
- Extended partition  

After fixing storage, installation completed successfully.

---

### ✅ Verification

- Wazuh dashboard accessed via browser  

📸 **Wazuh Dashboard**
![Wazuh Dashboard](../screenshots/wazuh-dashboard.png)

---

## 🔗 Agent Setup

The Wazuh agent was installed on Windows and connected to the server.

### ✅ Verification

- Agent successfully connected  

📸 **Agent Connected**
![Agent](../screenshots/wazuh-agent.png)

---

## 🔄 Sysmon + Wazuh Integration

Sysmon logs were forwarded to Wazuh for analysis.

### ✅ Verification

- Sysmon events visible in Wazuh  

📸 **Sysmon in Wazuh**
![Sysmon Wazuh](../screenshots/sysmon-wazuh.png)

---

## 📊 Final Status

| Component | Status |
|----------|--------|
| Sysmon | ✅ Working |
| SSH | ✅ Running |
| Wazuh Server | ✅ Running |
| Wazuh Agent | ✅ Connected |
| Log Integration | ✅ Working |

---

## 🧠 Key Learning

- Proper setup is required for accurate detection  
- Wazuh requires sufficient system resources  
- Sysmon significantly improves visibility into system activity  

---
