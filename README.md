# Jangow01 – From Enumeration to Root Access

## Overview
This report documents the compromise of the **Jangow01** machine from initial enumeration to full root access. The attack was performed from a Kali Linux machine in a controlled lab environment.

> **Note:** This content is for educational purposes only.

---

## Lab Setup
- **Attacker Machine:** Kali Linux  
- **Target Machine:** Jangow01  
- **Network Configuration:** Host-only network  

This ensured isolated communication between attacker and victim systems.

---

## Initial Enumeration

### Network Identification
The attacker machine IP was identified using:

```bash
ifconfig
#nmap -sTo identify active hosts within the network, scanning was performed to confirm the target system's availability.

Port Scanning

## port scan was conducted to identify exposed services:

nmap -sV <target-ip>
Observed Open Ports:
FTP (21)
HTTP (80)

The presence of these services indicated potential entry points for further exploration.

#Web Enumeration

Since HTTP (port 80) was open, the target IP was accessed through a browser.

Findings:
A section (/buscar) returned a blank page
This behavior suggested the possibility of hidden directories or files


Further probing revealed a sensitive directory:

http://<target-ip>/.backup
Credential Discovery

Inside the .backup directory, credentials were exposed.

Security Issues Identified:
Improper file handling
Sensitive data left accessible on the server

These credentials became the entry point for the next stage.

Initial Access via FTP

Since FTP service was open, it was used for gaining access.

Steps Performed:
ftp <target-ip>
Connected to FTP service
Authenticated using discovered credentials
Successfully accessed the target system
Exploitation Phase

An exploit was prepared on the attacker machine and transferred to the target system via FTP.

Example Transfer Method:
put exploit_file
This step leveraged:
Open FTP service
Weak access control

The exploit was uploaded successfully to the target machine.

Privilege Escalation

After gaining initial access, enumeration of the system revealed a kernel-level vulnerability.

Enumeration Example:
uname -a
Kernel Exploit Path Chosen Because:
It provided a direct escalation route
The system version matched known vulnerable kernels
Outcome:
Full root access achieved
Result

The system was successfully compromised through:

Initial access via exposed credentials
Privilege escalation via kernel exploit
Root-level control achieved
Key Observations
Exposed backup files can directly lead to credential leakage
FTP services significantly increase attack surface if not secured
Kernel vulnerabilities remain a critical escalation vector
Enumeration quality directly impacts attack success
Defensive Improvements
Restrict access to sensitive directories like .backup
Disable or secure FTP service
Regularly patch kernel vulnerabilities
Implement proper access control and monitoring
[proof.pdf](https://github.com/user-attachments/files/27191175/proof.pdf)
Notes

This report is based on a controlled CTF/lab scenario and reflects a structured attack methodology rather than automated exploitation.V <target-ip>
