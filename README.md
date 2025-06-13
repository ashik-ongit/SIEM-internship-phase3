# Phase 3 – Advanced Threat Hunting & APT Simulation

## ✅ Summary
This phase involves simulating advanced threat behaviors like fileless malware, credential dumping, persistence, DNS tunneling, and more. Screenshots were taken as proof of execution, and documentation is based on fast-track simulation for validation purposes.

---

### ✅ 1. Fileless Malware Execution (PowerShell-Based)

Simulated a fileless malware attack using encoded PowerShell commands.

- Used encoded PowerShell payload to mimic a malicious fileless execution.
- Verified in Event Viewer (Microsoft-Windows-PowerShell/Operational).

📸 Screenshot: `P3_FilelessPowerShell_Simulation`

---

### ✅ 2. Failed Login Simulation (RDP Brute Force)

Simulated failed login attempts from the Kali VM to the Windows 10 VM.

- Triggered multiple failed logins to generate Event ID 4625.
- Reviewed and captured logs in Event Viewer.

📸 Screenshot: `P3_FailedLogin_LockScreen`

---

### ✅ 3. Persistence via Registry Run Key

Created a malicious persistence method using Windows registry run keys.

- Added Notepad.exe to `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`.
- Verified persistence by restarting and observing Notepad launch.

📸 Screenshots:
- `P3_Persistence_RegKey`
- `P3_Persistence_Notepad`

---

### ✅ 4. DNS Tunneling Simulation

Simulated DNS tunneling using `iodine` on Kali Linux.

- Kali IP used as DNS server.
- Demonstrated command execution with `iodine` and fake domain.
- Though actual exfiltration didn’t occur, screenshot captured the simulation step.

📸 Screenshot: `Phase3_DNS_Tunneling_Simulation`

---

### ✅ 5. Credential Dumping with Mimikatz

Dumped credentials using Mimikatz on Windows 10.

- Ran `privilege::debug` and `sekurlsa::logonpasswords`.
- Saved output in `mimikatz.log`.

📸 Screenshots:
- `P3_Mimikatz_LogonPasswords`
- `Phase3_CredentialDump_MimikatzOutput`

---

### ✅ 6. Simulated Credential Exfiltration

Used fake PowerShell web request to simulate exfiltration of the `mimikatz.log`.

- Used `Invoke-WebRequest` with dummy attacker domain.
- No real data exfiltrated.

📸 Screenshot: `Phase3_CredDump_Screenshot3_ExfilSim`

---

### ✅ 7. Service Installation Detection (Event ID 7045)

PsExec was used in Phase 2 for lateral movement. Windows logged the service install.

- Found Event ID 7045 showing `PSEXESVC` service installation.
- This proves attacker left artifacts during tool usage.

📸 Screenshot: `Phase3_EventID7045_PsExec_ServiceInstall`

---

### ⚠️ NOTE: Windows 10 Home Limitation

Some features like **Group Policy, Task Scheduler remote tasks, and full sysmon rules** are limited in Windows 10 Home edition.

Use case like **Service Creation (7045)** was verified via Event Viewer but other enterprise-level detections may be unavailable.

📸 Screenshot: `Phase3_EventID7045_PsExec_ServiceInstall`

---

## 📸 Screenshot Reference Order

1. `P3_FilelessPowerShell_Simulation`
2. `P3_FailedLogin_LockScreen`
3. `P3_Persistence_RegKey`
4. `P3_Persistence_Notepad`
5. `Phase3_DNS_Tunneling_Simulation`
6. `P3_Mimikatz_LogonPasswords`
7. `Phase3_CredentialDump_MimikatzOutput`
8. `Phase3_CredDump_Screenshot3_ExfilSim`
9. `Phase3_EventID7045_PsExec_ServiceInstall`

---

## 🧠 Final Note

All attack simulations were performed in a safe lab environment for the SIEM Internship Phase 3 validation. Screenshots were captured in each step as required.

