
#  Wireshark – Network Packet Capture and Analysis Tool


## Procedure: Capturing Plaintext Passwords

### Step 1: Start Capturing Packets
- First, open Wireshark. You will see a list of all available network interfaces (e.g., "Wi-Fi," "Ethernet").


- Select the interface your computer is using to connect to the internet (in this case, Wi-Fi).

  <br>
   <br>
  <p align="center">
    <img width="1917" height="1018" alt="Screenshot 2025-11-11 124325" src="https://github.com/user-attachments/assets/3e2753b7-1ac6-4d0f-a6ec-3fd6713d2ad3" />

  </p>
  <br>
  <br>

- Click the blue shark fin icon 🦈 in the top-left corner to start the capture. Wireshark will immediately begin capturing all traffic passing through that interface.
 <br>
   <br>
  <p align="center">
    <img width="1916" height="1021" alt="Screenshot 2025-11-11 124348" src="https://github.com/user-attachments/assets/a5f62149-e73a-454d-8a5b-c01ed8058c35" />

 </p>
  <br>
  <br>

  ### Step 2: Generate Login Traffic
  - Open a web browser and navigate to http://testphp.vulnweb.com/login.php.

- Enter any dummy credentials. For this example, we'll use:

   Username: 12345

   Password: @12345@

- Click the login button. The login will fail, but the data has already been sent across the network.

 <br>
   <br>
  <p align="center">
    <img width="1592" height="886" alt="Screenshot 2025-11-11 124742" src="https://github.com/user-attachments/assets/a358d15c-5f23-4e30-92f8-20a6dff02bcd" />

 </p>
  
  
### step 3: Stop Capture and Filter Traffic

- Return to Wireshark and click the Stop button (the red square).

- In the display filter bar, you need to find the packet containing the login data. Since the form data was sent to the server, we will look for an HTTP POST request.

- Apply the following filter to find the exact packet and press Enter:

 <br>
   <br>
  <p align="center">

   <img width="1919" height="1016" alt="Screenshot 2025-11-11 133420" src="https://github.com/user-attachments/assets/773ebfa6-4775-4cd2-975e-9d9434dbdd09" />

 </p>
  <br>
  <br>

### step 4: Inspect the Packet to Find Credentials 

- In the filtered packet list, you should see a packet with information like "POST /userinfo.php". Select this packet.

- In the Packet Details pane below the list, expand the following sections:

Hypertext Transfer Protocol

HTML Form URL Encoded

- Inside the "HTML Form URL Encoded" section, you will see the credentials you entered in plaintext.

 <br>
   <br>
  <p align="center">
    <img width="1525" height="818" alt="image" src="https://github.com/user-attachments/assets/bbc85e44-79eb-48e5-921d-ec7a93756a33" />
    
 </p>
  <br>
  <br>

---

## Result
The experiment successfully intercepts the login credentials in a human-readable format. The analysis of the captured POST packet reveals the plaintext data that was transmitted over the network:

This result confirms the inherent security flaw of the HTTP protocol. Any sensitive data sent over HTTP is transmitted openly, making it trivial to intercept.
