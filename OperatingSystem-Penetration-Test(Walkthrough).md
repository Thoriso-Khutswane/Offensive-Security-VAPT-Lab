##  Operating System Penetration Testing – Metasploitable2

Target: Metasploitable2. Is an intentionally vulnerable virtual machine designed for training, exploit testing, and general target practice


### Step 1 — Identify Target IP Address

- The first step I performed was identifying the IP address of the operating system running on my Metasploitable2 virtual machine. To do this, I opened the Metasploitable2 terminal and entered the command **ifconfig**, as shown in the figure below. keep in mind that the IP can also be discorved by using **ping**. I just used this method because the system is already running on my virtual machine.
  
![bar plot]()

### Step 2 — Network Scanning using Nmap

- Using the IP address I gathered earlier, I performed a detailed scan to identify which ports were open on the Metasploitable2 machine. To do this, I used Nmap. I opened my Kali Linux terminal and executed the following command:
 
                                 nmap -sV -O [target IP]

In this command, -sV enables service version detection, -O enables operating system detection, and [target IP] refers to the server’s IP address,in this case, 192.168.56.102.

![bar plot]()

- The figure above shows the number of open ports detected on the operating system. The table below lists five open ports that are potentially vulnerable.


| Port Number | State | Service | Version                                      |
|-------------|--------|----------|-----------------------------------------------|
| 21/tcp      | open   | ftp      | vsftpd 2.3.4                                  |
| 22/tcp      | open   | ssh      | OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0) |
| 23/tcp      | open   | telnet   | Linux telnetd                                |
| 24/tcp      | open   | smtp     | Postfix smtpd                                |
| 25/tcp      | open   | domain   | ISC BIND 9.4.2                               |



### Step 3 — Detect FTP Backdoor

The FTP service was tested using an Nmap script.

- To check whether any of the open ports had a known backdoor associated with it, I focused on the port running the FTP service. Specifically, I examined vsftpd 2.3.4, which is known to have a backdoor vulnerability in certain compromised distributions. To test for this vulnerability, I used the following Nmap script command:

                   nmap --script ftp-vsftpd-backdoor -p 21 [target host]
  This script checks whether the vsftpd v2.3.4 service on port 21 is backdoored and vulnerable to unauthorized access.

![bar plot]()

From the results shown in the figure above, I observed that the Nmap script reported the vsftpd service as backdoored, indicating that the version running on port 21 contains the known vulnerability. The output also confirms that the backdoor is exploitable, meaning an attacker could potentially gain unauthorized access through this service.

 - Backdoor Information

| Backdoor Information        | State                    | Disclosure Date |
|-----------------------------|---------------------------|------------------|
| vsFTPd version 2.3.4 backdoor | Vulnerable (Exploitable) | 2011‑07‑04       |



### Step 4 — Exploit using Metasploit

- Now that I had identified a vulnerable service to target, I proceeded to exploit the machine. For this step, I used Metasploit. To launch Metasploit, I opened my Linux terminal and typed the following command:

      msfconsole

This command starts the Metasploit Framework console, which provides access to a wide range of exploitation modules. 

![bar plot]()

### Step 5 — Load Exploit Module

- To gain access to the operating system, I used the Metasploit module specifically designed for exploiting the vsftpd 2.3.4 backdoor. In the Metasploit console, I entered the following command:

      use exploit/unix/ftp/vsftpd_234_backdoor
  
 This module targets the vsftpd version 2.3.4 backdoor vulnerability that I previously identified using the Nmap script.

![bar plot]()

Set target host:

    set RHOSTS 192.168.56.102


### Step 6 — Shell Access

- The final step was to establish a session with the operating system and complete the exploitation process. To do this, I typed the command:

      run
  
Executing this command launched the exploit and created a session with the target machine. Once the session was established, I gained full access to the operating system through the Metasploit command line.

 ![bar plot]() 

In Figure 5.6 above, a session between the operating system and myself (the tester/attacker) has been successfully established, indicating that the exploitation was completed successfully. Since I selected a random open port to exploit, these results support the hypothesis that:
“The more open ports a system has, the higher the likelihood of successful attacks.”
