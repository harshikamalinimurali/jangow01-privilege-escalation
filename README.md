# Jangow01 – From Enumeration to Root Access

## Overview
This report documents the compromise of the **Jangow01** machine from initial enumeration to full root access. The attack was performed from a Kali Linux machine in a controlled lab environment.

> **Note:** This content is for educational purposes only.

---

## Lab Setup
* **Attacker Machine:** Kali Linux
* **Target Machine:** Jangow01
* **Network Configuration:** Host-only network

This ensured isolated communication between attacker and victim systems.

---

## Initial Enumeration

### Network Identification
The attacker machine IP was identified using:

```bash
ifconfig
