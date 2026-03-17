
## Web Application Penetration Testing – DVWA

**Target:** Damn Vulnerable Web Application (DVWA). DVWA is an intentionally vulnerable web application used to practice penetration testing techniques.

### Step 1:Configure Browser Proxy

To configure Firefox to work with Burp Suite, I first needed to adjust the browser’s settings. Burp Suite operates as a proxy between the tester (in this case, myself) and the target web application hosted on a server
**Note:** Follow the numbered arrows in ascending order for each step.

1. In the Firefox menu, I selected Preferences, as shown in the figure below.

   ![bar plot](https://github.com/Thoriso-Khutswane/Offensive-Security-VAPT-Lab/blob/main/Images/WebApp-VAPT-Images/1FirefoxPreferences.png)

2. In the Preferences search bar, I searched for the word ‘Proxy’ and then selected the result labeled ‘Network Settings’, as shown in the figure below.

    ![bar plot]()

3. On the Network Settings page, I selected “Manual proxy configuration.” I then entered 127.0.0.1 as the HTTP proxy, which is the localhost address where Burp Suite runs on port 8080. I made sure to check the option “Also use this proxy for FTP and HTTPS” and then clicked “OK” to complete the configuration, This allows Burp Suite to intercept all HTTP requests.
   
  - In computer networking, a proxy server acts as an intermediary between a client requesting a resource and the server providing that resource. In this setup, I used Burp Suite as the intermediary between the web server and myself as the tester.
    
  ![bar plot]()

### Step 2 : Intercept Login Request
    
1. I used Burp Proxy to intercept the authentication request sent to the server. 

-  To do this, I started Burp Suite on my Linux machine. Inside Burp Suite, I selected the “Proxy” tab, then opened “Intercept.” I made sure that “Intercept is on” before proceeding.

   ![bar plot]()

-  Next, I accessed the DVWA web application using Firefox. In the browser’s address bar, I entered the URL http://192.168.56.102/dvwa, which directed me to the DVWA login page. I logged in using the default credentials—username: admin and password: password—and selected “Login.”
  
**Note:** The IP address 192.168.56.102 is the local address of the Metasploitable2 machine, which serves as the host for the DVWA web application.

 ![bar plot]()

- After completing the previous step, I noticed that the login request page continued to load without progressing. This occurred because the proxy intercept was still enabled. When I checked Burp Suite, I could see the raw request data that had been captured during the login attempt. This confirmed that Burp Suite was successfully configured to function as a proxy between the server side and the client side of the web application.
Results:
The captured output clearly shows that Burp Suite intercepted the login request. The raw data contains the username and password I entered on the DVWA login page, demonstrating that the proxy configuration between Burp Suite and Firefox was successful.

 ![bar plot]()

### Step 3 :Send Request to Burp Intruder

- I then right‑clicked on the raw data window that Burp Suite captured earlier and selected “Send to Intruder,” as shown in the figure below.

   ![bar plot]()
  
### Step 4 :Configure Intruder Attack 

- Next, I selected “Intruder” in Burp Suite. Under the Intruder panel, I chose “2” and then selected “Positions.” In the Positions tab, I could see the full request that I had sent to Intruder. The highlighted sections indicate the values that can be targeted for brute‑forcing. To remove unnecessary highlighted fields, I selected the “Clear” button on the right‑hand side, as shown in the figure below.

 ![bar plot]()

- While in **Intruder → 2 → Positions**, I selected “Cluster bomb” as the attack type. The **Cluster Bomb** attack method tests all possible combinations of the payloads. In this setup, the first payload corresponds to the username, and the second payload corresponds to the password. Burp Suite will systematically try every username–password combination. 

   ![bar plot]()

- Next, I highlighted the values that I intended to brute‑force—specifically, the username field and the password field. After selecting each value, I clicked “Add” to include them as payload positions. This process is shown in the figure below

  ![bar plot]()

### Step 5 :Configure Username Payload

- I then navigated to the Payloads tab and set “Payload Set” to 1, which corresponds to the username payload. I selected “Simple list” as the payload type, since I planned to use a basic custom wordlist that I created myself. Under Payload Options, I entered several commonly used default usernames, such as **administrator, admin, root, user, and test**.
If needed, Burp Suite also allows uploading an external file containing usernames or passwords, but in this case, I manually entered the values we prepared.


  ![bar plot]()

### Step 6 :Configure Password Payload

- Next, I set “Payload Set” to 2, which corresponds to the password field. I then added a list of common default passwords—such as pass, password, 1234, and root—to the payload options box.

   ![bar plot]()

### Step 7 :Launch Brute Force Attack

- Selected a button that says, “start attack"

  ![bar plot]()


### Step 8 :Successful Authentication

- After clicking “Start attack,” a pop‑up window titled **“Intruder Attack 1”** appeared. This is where I could determine whether the brute‑force attempt was successful. The table displayed several useful details, and the first thing I noticed was that most of the entries in the Length column were identical. Because of this, I looked for the entry with a different response length—4948—which corresponded to the credentials admin and password.
I selected that row and then opened the “Response” tab. Under Response, I selected “Render” to view the rendered page and confirm the successful login.

![bar plot]()

- After selecting Render, the DVWA welcome page appeared with the message “Welcome to the password‑protected area, admin.” This confirmed that the brute‑force attack was successful and that I had gained access to the application as the admin user. The figure below illustrates the result.

  ![bar plot]()
