# Penetration Testing Report

**Target Name:** Simple CTF Machine  
**IP Address:** 10.48.132.190  
**Assessment Type:** Capture The Flag (CTF) / Educational Penetration Test  
**Tester:** Keshav  
**Date:** __________  
**Methodology:** Black-Box Testing

---

## 1. Executive Summary

This report documents the penetration testing activities conducted against the target system **10.48.132.190** as part of a controlled CTF environment. The objective of the assessment was to identify vulnerabilities, exploit misconfigurations, and obtain user-level and root-level access.

The assessment revealed multiple security weaknesses, including anonymous FTP access, exposed CMS services, weak credentials, and improper sudo permissions. These issues were chained together to achieve full system compromise.

---

## 2. Scope of Assessment

- **In-Scope IP:** 10.48.132.190  
- **Services Tested:** FTP, HTTP, SSH  
- **Out-of-Scope:** Denial of Service (DoS), Social Engineering

---

## 3. Reconnaissance and Enumeration

### 3.1 Network Scanning (Nmap)

An Nmap scan was conducted to identify open ports, running services, and service versions.

**Open Ports Identified:**

- **21/tcp** – FTP (vsftpd 3.0.3)
- **80/tcp** – HTTP (Apache 2.4.18)
- **2222/tcp** – SSH (OpenSSH 7.2p2)

**Key Observations:**

- Anonymous FTP login was enabled.
- A web application was hosted on port 80.
- SSH was running on a non-standard port.

📸 *Screenshot Placeholder – Nmap Scan Output*

---

### 3.2 FTP Enumeration

Anonymous FTP login was successful. During enumeration, a file named **formitch.txt** was discovered, revealing a valid system username.

**Findings:**

- Anonymous FTP access enabled
- Username identified: **mitch**

📸 *Screenshot Placeholder – FTP Anonymous Login & File Discovery*

---

### 3.3 Web Enumeration (HTTP)

Analysis of `robots.txt` revealed a hidden directory.

- **/simple/** → CMS Made Simple **version 2.2.8**

This CMS version is known to be vulnerable to credential-based attacks.

📸 *Screenshot Placeholder – robots.txt and /simple Directory*

---

## 4. Exploitation

### 4.1 Credential Attack (SSH)

Using the discovered username **mitch**, a password attack was performed and valid credentials were obtained.

- **Username:** mitch  
- **Password:** secret

SSH access was established using the following command:

```bash
ssh mitch@10.48.132.190 -p 2222
