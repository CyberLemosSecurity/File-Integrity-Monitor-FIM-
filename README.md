#  File Integrity Monitor (FIM)

##  Description
This project focuses on the development of a robust **File Integrity Monitor (FIM)** using PowerShell and SHA-256 hashing. The tool is designed to monitor critical directories in real-time, detecting unauthorized file modifications, creations, and deletions. This lab simulates the core functionality of a **HIDS (Host-based Intrusion Detection System)**, a fundamental requirement for security compliance frameworks such as PCI DSS and NIST.

##  Objectives
* **Implement** a monitoring system based on Cryptographic Hashing.
* **Establish** a structured Security Baseline in JSON format for auditing.
* **Develop** a Persistent Logging mechanism for forensic analysis and SIEM integration.
* **Validate** detection efficacy against simulated Ransomware attacks and file tampering.

## 🛠️ Technologies & Tools
* **PowerShell:** Main engine for automation and data collection.
* **SHA-256 Algorithm:** Ensuring data integrity and resistance against collision attacks.
* **JSON:** Data structure used for secure baseline storage.
* **Windows Environment:** Target environment for monitoring critical system files.

##  Project Architecture
The lab is structured into three logical phases:

* **Baseline Generation:** A recursive scan of the target directory to generate unique digital signatures for every file.
* **Real-Time Monitoring:** A continuous comparison loop between the current file state and the established baseline.
* **Alerting & Logging:** Multi-color console feedback for rapid triage and event persistence in an `alerts.log` file.

##  How to Run

### 1. Environment Setup
Ensure the following directory structure exists:
* `C:\Labs\FIM-Project\Target` (Monitored files)
* `C:\Labs\FIM-Project\System` (Baseline and Logs)

### 2. Create the Baseline
Run the `Create-Baseline.ps1` script as an Administrator to record the "known good" state of the system.

### 3. Start Monitoring
Execute the `Monitor-Integrity.ps1` script. The terminal will enter active listening mode.

##  Evidence (Proof of Concept)
The following screenshot demonstrates the FIM detecting three simultaneous threat vectors:
* **Red:** Critical configuration file (`config.ini`) modified.
* **Cyan:** Suspicious binary injection (`hack.exe`).
* **Yellow:** Removal of defense scripts (`backup.ps1`).
<img width="1342" height="377" alt="image" src="https://github.com/user-attachments/assets/669e7e37-140e-4345-a3a0-f9a8ce7f6ae7" />

##  Strategic Analysis (Blue Team Insights)
This implementation focuses on key defensive security principles:
* **Integrity Validation:** SHA-256 ensures that even a single-bit change in a configuration file is detected.
* **Evidence Persistence:** The logging system (`alerts.log`) preserves indicators of compromise (IoCs) even if the attacker attempts to clear terminal history.
* **Future Roadmap:** This FIM will be integrated with my **Ransomware Simulation** lab to measure response times against mass-encryption events.











