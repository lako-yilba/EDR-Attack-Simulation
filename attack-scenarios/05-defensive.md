# ⚫ Defense Evasion (Log Clearing)

## 📌 Overview

In this stage, defense evasion was simulated by clearing system logs to hide evidence of the attack.

This demonstrates how attackers attempt to remove traces of their activity after compromising a system.

---

## 🎯 Objective

- Remove evidence of attack activity  
- Simulate attacker evasion techniques  
- Analyze detection of log clearing  

---

## ⚙️ Lab Setup

- Attacker Machine: Kali Linux  
- Target Machine: Windows  
- Tool Used: Windows Command  

---

## ⚔️ Attack Execution

After completing the attack chain, logs were cleared using a Windows command.

### 🔹 Step 1 — Open Shell


shell


---

### 🔹 Step 2 — Clear Logs


wevtutil cl Security


---

## ✅ Result

- Security logs were cleared  
- Previous event records removed from the system  

---

📸 **Log Clearing Command**
![Log Clear](../screenshots/msf3.png)

---

## 📊 Log Analysis

### 🪟 Windows Logs

Even though logs were cleared, Windows generated a new event:

- Event ID: **1102**
- Description: Audit log cleared  

---

### 🛡️ Wazuh Detection

The following query was used:


data.win.system.eventID: 1102


### 🔍 Observations

- Log clearing activity detected  
- Indicates attempt to remove evidence  
- Strong indicator of malicious behavior  

(Note: Log clearing was performed and verified, but specific Wazuh alert screenshot was not captured.)

---

## 🧠 Analysis

- Attackers clear logs to hide their actions  
- However, log clearing itself generates a detectable event  
- Centralized logging (Wazuh) helps retain evidence even after deletion  

---

## 🧬 MITRE ATT&CK Mapping

- **T1070 — Indicator Removal on Host**

---

## 🧠 Key Learnings

- Log clearing is a common evasion technique  
- Even evasion attempts leave traces  
- SIEM tools are critical for retaining and analyzing logs  

---

## 🧾 Conclusion

Defense evasion was successfully simulated by clearing system logs. The activity was still detectable through Event ID 1102, demonstrating how attackers attempt to hide evidence and how such actions can still be identified.
