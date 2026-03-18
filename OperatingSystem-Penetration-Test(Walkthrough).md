##  Operating System Penetration Testing – Metasploitable2

Target: Metasploitable2. Is an intentionally vulnerable virtual machine designed for training, exploit testing, and general target practice


### Step 1 — Identify Target IP Address

- The first step I performed was identifying the IP address of the operating system running on my Metasploitable2 virtual machine. To do this, I opened the Metasploitable2 terminal and entered the command **ifconfig**, as shown in the figure below. keep in mind that the IP can also be discorved by using **ping**. I just used this method because the system is already running on my virtual machine.
  
![bar plot]()

### Step 2 — Network Scanning using Nmap

- Using the IP address I gathered earlier, I performed a detailed scan to identify which ports were open on the Metasploitable2 machine. To do this, I used Nmap. I opened my Kali Linux terminal and executed the following command:
 
                                 nmap -sV -O [target IP]

![bar plot]()

- The figure above shows the number of open ports detected on the operating system. The table below lists five open ports that are potentially vulnerable.


| Port Number | State | Service | Version                                      |
|-------------|--------|----------|-----------------------------------------------|
| 21/tcp      | open   | ftp      | vsftpd 2.3.4                                  |
| 22/tcp      | open   | ssh      | OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0) |
| 23/tcp      | open   | telnet   | Linux telnetd                                |
| 24/tcp      | open   | smtp     | Postfix smtpd                                |
| 25/tcp      | open   | domain   | ISC BIND 9.4.2                               |







