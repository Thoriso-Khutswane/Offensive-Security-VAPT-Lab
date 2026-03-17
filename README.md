# Vulnerability Assessment and Penetration Testing Lab

## Overview

This repository documents the practical implementation of my **Honours Research Project in Computer Science at North-West University** & my practical working experience at Momentum Group Limited as an Associate Pentester .

The project focuses on performing **Vulnerability Assessment and Penetration Testing (VA-PT)** on both:

* Web Applications
* Operating Systems

The experiments were conducted in a **controlled virtual penetration testing lab environment** using intentionally vulnerable systems.

The objective of this project was to demonstrate how attackers exploit security weaknesses and how organizations can detect and mitigate these vulnerabilities.

---

# Lab Environment

The penetration testing environment was implemented using **Oracle VirtualBox**.

## Attacker Machine

* Kali Linux

## Target Systems

* Metasploitable2 (vulnerable operating system)
* DVWA (Damn Vulnerable Web Application)

---

# Lab Architecture

!ExecutiveOverview.png

![bar plot](https://github.com/Thoriso-Khutswane/Offensive-Security-VAPT-Lab/blob/main/ExecutiveOverview.png)


# Tools Used

| Tool            | Purpose                      |
| --------------- | ---------------------------- |
| Kali Linux      | Penetration testing platform |
| Burp Suite      | Web application testing      |
| Nmap            | Network scanning             |
| Metasploit      | Exploitation framework       |
| DVWA            | Vulnerable web application   |
| Metasploitable2 | Vulnerable Linux server      |

---

# Penetration Testing Methodology

The project follows a simplified **VA-PT lifecycle**:

1. Information Gathering
2. Vulnerability Scanning
3. Attack Development
4. Exploitation
5. Result Analysis

---

# Web Application Penetration Testing

Target: **DVWA Web Application**

Attack Method:

* Brute Force Authentication Attack

Tool Used:

* Burp Suite Intruder

📷 **Insert screenshots**

Examples:

```
WebApp-Penetration-Test/screenshots/burp_proxy.png
WebApp-Penetration-Test/screenshots/login_request.png
WebApp-Penetration-Test/screenshots/bruteforce_results.png
```

---

# Operating System Penetration Testing

Target: **Metasploitable2**

Attack Method:

* FTP Backdoor Exploit

Tools Used:

* Nmap
* Metasploit

📷 **Insert screenshots**

Examples:

```
OS-Penetration-Test/screenshots/nmap_scan.png
OS-Penetration-Test/screenshots/metasploit_shell.png
```

---

# Key Findings

The results revealed several common security weaknesses:

* Default credentials significantly increase the likelihood of compromise
* Exposed open ports increase the attack surface
* Outdated services contain exploitable vulnerabilities
* Weak authentication mechanisms allow brute force attacks

---

# Skills Demonstrated

This project demonstrates the following cybersecurity skills:

* Web Application Penetration Testing
* Network Enumeration
* Vulnerability Analysis
* Exploitation Techniques
* Red Team Simulation
* Security Reporting

---

# Disclaimer

This project was conducted in a **controlled laboratory environment** for academic purposes.

All systems tested were **intentionally vulnerable**.

