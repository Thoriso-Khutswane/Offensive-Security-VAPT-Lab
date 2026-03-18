# Vulnerability Assessment and Penetration Testing Lab

## Overview

This repository documents the practical implementation of my Honours Research Project in Computer Science at North‑West University, as well as my three‑month practical work experience at Momentum Group Limited.

The project focuses on performing **Vulnerability Assessment and Penetration Testing (VA-PT)** on both:

-  Web Application
-  Operating System

The experiments were conducted in a **controlled virtual penetration testing lab environment** using intentionally vulnerable systems.

The objective of this project was to demonstrate how attackers exploit security weaknesses and how organizations can detect and mitigate these vulnerabilities.

---

# Lab Environment

The penetration testing environment was implemented using **Oracle VirtualBox**.

## Attacker Machine

* Kali Linux

## Target Systems

* Metasploitable2 (vulnerable operating system,also used to host the DVWA)
* DVWA (Damn Vulnerable Web Application)

Both systems were downloaded and installed in the Oracle Virtual Box
* Metasploitable2 download link: https://www.vulnhub.com/entry/metasploitable-2,29/
* DVWA ISO image download link: https://www.vulnhub.com/entry/damn-vulnerable-web-application-dvwa-107,43/
---

# Lab Architecture


![bar plot](https://github.com/Thoriso-Khutswane/Offensive-Security-VAPT-Lab/blob/main/Images/LabArchitecture2.png)


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
2. Vulnerability Scanning(Nessus, Burp Suite, ZAP, & etc. can be utilized)
3. Attack Development
4. Exploitation
5. Result Analysis

---

# Web Application Penetration Testing

Target: **DVWA Web Application** hosted on metasploitable2 which is also the operating system that is exploited in this project.

Attack Method: Brute Force Authentication Attack

Tools Used: Kali Linux, Burp Suite & Firefox 

![bar plot](https://github.com/Thoriso-Khutswane/Offensive-Security-VAPT-Lab/blob/main/Images/WebApp-VAPT-Images/13IntruderAttack1Window.png)

![bar plot](https://github.com/Thoriso-Khutswane/Offensive-Security-VAPT-Lab/blob/main/Images/WebApp-VAPT-Images/14BruteforceSuccesful.png)



# Operating System Penetration Testing

Target: **Metasploitable2**

Attack Method: FTP Backdoor Exploit

Tools Used: Kali Linux,Nmap, Metasploit


  - Nmap Scrip-FTP backdoor identification 
![bar plot](https://github.com/Thoriso-Khutswane/Offensive-Security-VAPT-Lab/blob/main/Images/OperatingSystem-VAPT-Images/3NmapFTPBackdoorIdentificationScript.jpg)

- Session succesfully created
![bar plot](https://github.com/Thoriso-Khutswane/Offensive-Security-VAPT-Lab/blob/main/Images/OperatingSystem-VAPT-Images/6SessionCreated.jpg)



# Key Findings

The results revealed several common security weaknesses:

* Default credentials significantly increase the likelihood of compromise
* Exposed open ports increase the attack surface
* Outdated services contain exploitable vulnerabilities
* Weak authentication mechanisms allow brute force attacks


# Results Analysis

# Remediations

**To mitigate the identified webapp vulnerability developers are encouraged to:**

- Enforce strong password policies

- Implement account lockout after multiple failed attempts

- Add rate limiting

- Use CAPTCHA

- Enable Multi-Factor Authentication (MFA)

- Monitor and log authentication attempts

**To mitigate the identified vulnerability on the operating system computer networking professionals and system administrators are encouraged to:**

- Upgrade vsFTPd to a secure version

- Remove or disable FTP if not required

- Use secure alternatives (e.g., SFTP)

- Apply regular patch management

- Restrict access using firewall rules



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

