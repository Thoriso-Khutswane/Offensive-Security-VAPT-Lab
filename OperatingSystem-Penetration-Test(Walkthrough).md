##  Operating System Penetration Testing – Metasploitable2

Target: Metasploitable2. Is an intentionally vulnerable virtual machine designed for training, exploit testing, and general target practice


### Step 1 — Identify Target IP Address

- The first step I performed was identifying the IP address of the operating system running on my Metasploitable2 virtual machine. To do this, I opened the Metasploitable2 terminal and entered the command **ifconfig**, as shown in the figure below. keep in mind that the IP can also be discorved by using **ping**. I just used this method because the system is already running on my virtual machine.
  
![bar plot]()

### Step 2 — Network Scanning using Nmap

- Using the IP address I gathered earlier, I performed a detailed scan to identify which ports were open on the Metasploitable2 machine. To do this, I used Nmap. I opened my Kali Linux terminal and executed the following command:
 
                                 nmap -sV -O [target IP]

![bar plot]()
