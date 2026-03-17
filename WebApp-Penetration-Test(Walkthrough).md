
## Web Application Penetration Testing – DVWA

**Target:** Damn Vulnerable Web Application (DVWA). DVWA is an intentionally vulnerable web application used to practice penetration testing techniques.

### Step 1:Configure Browser Proxy

To configure Firefox to work with Burp Suite, I first needed to adjust the browser’s settings. Burp Suite operates as a proxy between the tester (in this case, myself) and the target web application hosted on a server
**Note:** Follow the numbered arrows in ascending order for each step.

1. In the Firefox menu, I selected Preferences, as shown in the figure below.

   ![bar plot]()

2. In the Preferences search bar, I searched for the word ‘Proxy’ and then selected the result labeled ‘Network Settings’, as shown in the figure below.

    ![bar plot]()

3. On the Network Settings page, I selected “Manual proxy configuration.” I then entered 127.0.0.1 as the HTTP proxy, which is the localhost address where Burp Suite runs on port 8080. I made sure to check the option “Also use this proxy for FTP and HTTPS” and then clicked “OK” to complete the configuration, as shown in the figure below.
   
In computer networking, a proxy server acts as an intermediary between a client requesting a resource and the server providing that resource. In this setup, I used Burp Suite as the intermediary between the web server and myself as the tester.

    
   


   
