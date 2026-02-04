# Secure Linux Infrastructure for Web & Database
**An Enterprise-Grade Defense-in-Depth Implementation**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform: Debian](https://img.shields.io/badge/Platform-Debian%2012-red.svg)](https://www.debian.org/)
[![SIEM: Wazuh](https://img.shields.io/badge/SIEM-Wazuh%204.7-blue.svg)](https://wazuh.com/)

## 🛡️ Project Overview
This project demonstrates a robust 3-tier security architecture designed to protect critical web and database assets. By transitioning from passive perimeter defense to an active, layered security posture, the infrastructure mitigates modern threats like SQL Injection, Brute-Force, and Lateral Movement.

### **Key Features**
- **3-Tier Architecture:** Isolated Web, Database, and Management planes.
- **Identity & Access:** Multi-Factor Authentication (MFA) via Google Authenticator + ED25519 SSH Keys.
- **WAF Integration:** Apache hardened with ModSecurity and OWASP Core Rule Set (CRS).
- **Centralized SIEM/XDR:** Real-time monitoring and log correlation using Wazuh.
- **Automated Response:** Active response triggers to block malicious IPs via iptables/Fail2Ban.
- **PKI Management:** Local Certificate Authority managed via XCA for end-to-end SSL/TLS encryption.

## 🏗️ Architecture


## 🚀 Implementation Details
### **1. Web Tier (Hardening)**
- **Server:** Apache2 on Debian 12.
- **Firewall:** ModSecurity (SecRuleEngine On) + OWASP CRS.
- **Encryption:** SSL/TLS certificates issued via custom Root CA.

### **2. Database Tier (Isolation)**
- **Engine:** MariaDB 10.11.
- **Access Control:** Iptables restricted to allow only Web-Tier IP on Port 3306.

### **3. Management Tier (Wazuh SIEM)**
- **Custom Decoders:** Developed XML decoders for PHP application-level logs.
- **Active Response:** Configured automated IP banning for Level 12+ security events.

## 🛠️ Tech Stack
- **OS:** Debian 12 (Bookworm)
- **Security:** Wazuh, ModSecurity, Fail2Ban, Google Authenticator (PAM)
- **Networking:** Iptables, XCA (PKI)
- **Database:** MariaDB

## 📂 Project Structure
```text
├── configs/            # Hardening scripts and service configs
│   ├── wazuh/          # Custom XML decoders and rules
│   ├── apache/         # ModSecurity and SSL configurations
│   └── firewall/       # Iptables rulesets
├── docs/               # Project documentation and reports
└── scripts/            # Automation and setup scripts
