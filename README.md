
# 🔐 EDR Attack Simulation (Wazuh + Sysmon)

## 📌 About this project

In this project, I built a home lab to simulate a real-world cyber attack and detect it using **Sysmon** and **Wazuh**.

The goal was to understand:
- how attackers perform different stages of an attack  
- how these activities can be detected using logs  

---

## 🧱 Lab Setup


Kali Linux (Attacker)
↓
Windows (Sysmon + Wazuh Agent)
↓
Ubuntu (Wazuh Server + Dashboard)


- Sysmon was used for detailed system logs  
- Wazuh was used for monitoring and detection  

---

## ⚔️ Attack Chain

I simulated a full attack step-by-step:

1. **Brute Force** — Gained initial access  
2. **Reverse Shell** — Got remote control  
3. **Credential Dumping** — Extracted passwords  
4. **Persistence** — Maintained access  
5. **Defense Evasion** — Cleared logs  

---

## 🛡️ Detection

Each attack stage was detected using Wazuh and Windows logs:

| Activity | Event ID |
|--------|---------|
| Failed Login | 4625 |
| Process Creation | 4688 |
| Credential Dumping | 10 |
| Registry Changes | 13 |
| Log Clearing | 1102 |

---

## 📁 Project Structure


setup/ → Lab setup
attack-scenarios/ → Step-by-step attacks
screenshots/ → Proof (logs + attacks)
report/ → Final incident report


---

## 📸 Screenshots

All screenshots are included in the `/screenshots` folder, showing:

- Attack execution  
- System logs  
- Wazuh detection  

---

## 🧠 What I learned

- How real-world attacks happen step-by-step  
- How logs help detect malicious activity  
- Importance of centralized logging (Wazuh)  
- Some attacks can be partially blocked but still detected  

---

## ⚠️ Note

This project was done in a controlled lab environment for learning purposes only.

---

