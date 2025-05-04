# Secure Server - HackTheBox Challenge

## Category
**Web Exploitation**

## Authors
- Vishal Suman  
- Youssef Elmorsi  
- Jean-Charles Hekamanu

---

## 🧠 Objective

This project focuses on identifying and exploiting vulnerabilities in a simulated secure server environment provided by HackTheBox (HTB). The challenge included:

- Reconnaissance and information gathering  
- Vulnerability identification  
- Exploitation (LFI, webshell deployment)  
- Privilege escalation attempts  
- Secure code patching and validation

---

## 🛠️ Tools and Techniques Used

- **Nmap** – Network and service enumeration  
- **Netcat (nc)** – Banner grabbing and manual service interaction  
- **Docker** – Local secure server replication  
- **cURL** – HTTP requests and LFI exploitation  
- **Samba (SMB)** – File sharing and webshell deployment via CIFS mount  
- **PHP** – Secure code validation and patching  

---

## 🔍 Vulnerability Identification Process

1. Connected to HTB using OpenVPN or PWN and retrieved the target IP.
2. Confirmed connectivity using ping.
3. Performed network enumeration using `nmap` and `nc`.
4. Identified potential vulnerabilities including **OpenSSL CVE-2024-6387** and **SMB exposure** on ports 139 and 445.

---

## ⚙️ Local Exploitation via Docker

Docker environment included:
- Nginx (Web Server)  
- PHP-FPM (PHP Processing)  
- Samba (File Sharing)

LFI and Log Poisoning attempts were conducted using `curl` and User-Agent header injection.

---

## 🐚 Webshell Deployment via Samba

```bash
sudo mount -t cifs //172.17.0.2/app /mnt/ -o username=guest,port=445

✅ Status
 LFI vulnerability exploited

 Webshell deployed via Samba

 PHP logic patched to prevent further exploitation

 Checker validation incomplete (port 1337 closed)

📌 Conclusion
This challenge demonstrated:

The real-world risks of insecure file inclusion

The power of service enumeration and manual fuzzing

Importance of secure PHP coding and input validation

How file-sharing services like Samba can be leveraged for exploitation

🔒 Recommendations
Always validate and sanitize user input

Harden Samba configurations and avoid guest access

Regularly patch PHP and underlying services

Monitor and restrict access to sensitive services like RPC and SMB
