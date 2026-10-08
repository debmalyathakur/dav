# WebDAV Penetration Testing Walkthrough

## 📌 Overview

This repository documents my hands-on penetration testing walkthrough of a vulnerable WebDAV-enabled Linux machine.

The assessment covers the complete attack path, starting from **network reconnaissance and service enumeration**, followed by **WebDAV discovery, authentication testing, file-upload validation, initial access, and local privilege escalation**.

> **Note:** The complete technical walkthrough, commands, screenshots, and Proof of Concept (PoC) are provided in the accompanying PDF.

---

## 🎯 Objectives

* Perform initial network reconnaissance
* Identify exposed services and technologies
* Enumerate the HTTP service and WebDAV endpoint
* Assess WebDAV authentication
* Validate file upload and execution capabilities
* Obtain initial access
* Enumerate local privileges
* Identify a `sudo` misconfiguration
* Complete privilege escalation in the lab environment

---

## 🔎 Attack Path

```text
Network Enumeration
        ↓
Apache HTTP Service
        ↓
WebDAV Discovery
        ↓
Authentication Weakness
        ↓
WebDAV Access via Cadaver
        ↓
File Upload Testing
        ↓
Server-Side File Execution
        ↓
Initial Access
        ↓
Privilege Enumeration
        ↓
Sudo Misconfiguration
        ↓
Root Access
```

---

## 🛠️ Tools Used

| Tool        | Purpose                                  |
| ----------- | ---------------------------------------- |
| **Nmap**    | Port, service and HTTP enumeration       |
| **Cadaver** | WebDAV interaction and file management   |
| **DAVTEST** | Testing WebDAV file upload and execution |
| **Netcat**  | Lab-based connection handling            |
| **Browser** | Manual WebDAV authentication testing     |

---

## 🔑 Key Findings

### 1. Exposed WebDAV Service

HTTP enumeration identified an accessible `/webdav/` endpoint protected by authentication.

### 2. Default Credentials

The WebDAV service was configured with publicly documented default credentials, allowing authenticated access to the WebDAV directory.

### 3. Unsafe File Upload Configuration

Testing demonstrated that the WebDAV service permitted file uploads and that PHP content could be processed by the server. This significantly increased the impact of the authentication weakness.

### 4. Initial Access

The vulnerable configuration was leveraged to obtain initial access to the target system as the web-service account.

### 5. Sudo Misconfiguration

Local privilege enumeration revealed that the compromised account could execute `/bin/cat` through `sudo` without requiring a password.

This configuration created an unintended privileged file-read capability and was subsequently leveraged for privilege escalation.

---

## 📊 Impact

The combination of **default WebDAV credentials, unrestricted file-upload functionality, server-side execution, and excessive sudo privileges** resulted in a complete compromise of the lab machine.

**Attack impact:**

```text
Unauthorized WebDAV Access
        +
Arbitrary File Upload
        +
Server-Side Execution
        +
Privilege Escalation
        =
Full System Compromise
```

---

## 🛡️ Recommended Remediation

* Remove or change all default credentials.
* Use strong, unique authentication credentials.
* Disable WebDAV if it is not required.
* Restrict WebDAV access to trusted users and networks.
* Prevent execution of uploaded server-side scripts.
* Apply appropriate file-upload restrictions.
* Review and minimize `sudo` privileges.
* Follow the principle of least privilege.
* Regularly audit exposed services and authentication configurations.

---

## 📄 Detailed Walkthrough

The complete assessment is available in the accompanying PDF, including:

* Detailed Nmap enumeration
* WebDAV discovery
* Authentication testing
* Cadaver usage
* DAVTEST results
* Initial-access PoC
* Local enumeration
* Sudo privilege analysis
* Privilege-escalation process
* Screenshots and evidence

---

## ⚠️ Disclaimer

This project was performed in an **authorized lab/CTF environment** for educational and cybersecurity learning purposes.

Do not attempt to access or exploit systems without explicit authorization.

---
## Author

**Debmalya Thakur**

Junior System Administrator | Aspiring Penetration Tester | VAPT Enthusiast

GitHub: https://github.com/debmalyathakur

LinkedIn: https://www.linkedin.com/in/debmalya-thakur-9b240417b

---

## 👨‍💻 Skills Demonstrated

**Reconnaissance • Network Enumeration • Web Enumeration • WebDAV Security Testing • Authentication Testing • File Upload Testing • Initial Access • Linux Enumeration • Privilege Escalation • Vulnerability Analysis • Penetration Testing**
