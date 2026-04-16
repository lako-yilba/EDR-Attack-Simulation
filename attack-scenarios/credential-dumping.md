# 🟣 Credential Dumping (Mimikatz / LSASS)

## 📌 Overview

In this stage, credential dumping was performed to simulate how attackers extract sensitive information such as usernames and passwords from memory.

This was achieved by accessing LSASS (Local Security Authority Subsystem Service), which stores authentication data.

---

## 🎯 Objective

- Extract credentials from system memory  
- Simulate real-world credential theft  
- Analyze detection through logs  

---

## ⚙️ Lab Setup

- Attacker Machine: Kali Linux  
- Target Machine: Windows  
- Tool Used: Meterpreter (Kiwi module)  

---

## ⚔️ Attack Execution

After gaining access through a reverse shell, credential dumping was performed.

### 🔹 Step 1 — Access Meterpreter Session
meterpreter >


---

### 🔹 Step 2 — Privilege Escalation


getsystem


---

### 🔹 Step 3 — Load Kiwi Module


load kiwi


---

### 🔹 Step 4 — Dump Credentials

Since `creds_all` did not work properly, LSASS dumping was used:


lsa_dump_sam


---

## ✅ Result

Credentials were successfully extracted from memory.

Example output:


Username: testuser
NTLM Hash: ************


This confirms that sensitive authentication data can be accessed by attackers.

---

📸 **Credential Dump Output**
![Credentials](../screenshots/cd.png)

---

## 📊 Log Analysis

### 🪟 Windows / Sysmon Logs

- LSASS process was accessed  
- Suspicious memory access behavior observed  

---

### 🛡️ Wazuh Detection

The following query was used:


data.win.system.eventID: 10


### 🔍 Observations

- Process attempted to access LSASS  
- Suspicious behavior indicating credential dumping  
- Activity correlated with attack timeline  

---

(Note: Specific Wazuh log screenshot was not captured, but the activity was verified through log queries.)

---
## 🧠 Analysis

- LSASS stores sensitive authentication data  
- Accessing LSASS is a strong indicator of credential dumping  
- Attackers use tools like Mimikatz to extract credentials  
- Detection relies on monitoring process behavior  

---

## 🧬 MITRE ATT&CK Mapping

- **T1003 — Credential Dumping**

---

## 🧠 Key Learnings

- Credentials stored in memory can be extracted if system is compromised  
- LSASS access is a critical detection point  
- Not all dumping methods work due to system protections  
- Alternate techniques can still succeed  

---

## 🧾 Conclusion

Credential dumping was successfully performed using LSASS memory access. The activity was detected through system logs and analyzed using Wazuh, demonstrating how attackers extract sensitive data after gaining access. 
