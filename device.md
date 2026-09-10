**Environment Details:** **Target Device URL:** 

### **Case 1: Same User, Same Device, Different Browsers**

**Test User:** `venkatesan.sivanandan@view.com` **Browsers Used:** Google Chrome, Microsoft Edge

- **Given:** The user is logged into the Guacamole portal simultaneously on both Chrome and Edge.
    
- **When:** The user initiates an RDP session to the device via Chrome and successfully connects, AND THEN attempts to connect to the exact same device via the Edge browser.
    
- **Then:** The new session in Edge becomes active, and the previous session in Chrome is immediately disconnected.
    
- **Conclusion:** When a single user attempts to access the same device from multiple browsers, the system allows only one active session at a time, prioritizing the newest connection.
    

### **Case 2: Different Users, Same Device, Different Browsers**

**Test User 1:** `venkatesan.sivanandan@view.com` (using Edge) **Test User 2:** `naveen.arockiaraj@neeve.ai` (using Chrome)

- **Given:** Two distinct users are logged into the Guacamole portal on their respective browsers.
    
- **When:** User 1 initiates an RDP session to the device via Edge and successfully connects, AND THEN User 2 attempts to connect to the exact same device via Chrome.
    
- **Then:** A conflict occurs where only one session is permitted. The connection allows only one active session at a time, causing one user's session to be disconnected while the other remains active.
    
- **Conclusion:** The system strictly enforces a limit of one concurrent session per device, even when different authenticated users are attempting access.
    

### **Case 3: Same User, Same Device, Same Browser (Multiple Tabs/Windows)**

**Test User:** `venkatesan.sivanandan@view.com` **Browser Used:** Google Chrome

- **Given:** The user is logged into the Guacamole portal using a single browser (Chrome).
    
- **When:** The user initiates an RDP session to the device in one tab and successfully connects, AND THEN attempts to open a second session to the exact same device in a new tab or window within the same browser.
    
- **Then:** The newly opened session becomes active, and the previous session is automatically logged out/disconnected.
    
- **Conclusion:** Even within the same browser session, attempting to open multiple connections to the same device forces the termination of the older connection.