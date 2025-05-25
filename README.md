# Security Foundations Project: PKI Setup and Client Connection

Student: Staroshchuk Kirill (anakata) 

Course: Security Foundations  
Professor: Maksymilian Marcinkowski  
Date: May 25, 2025

---

## 🚀Project Overview

This repository contains the implementation of a Public Key Infrastructure (PKI) environment, where I set up a private Certificate Authority (CA) using SmallStep. The project demonstrates how to create and configure certificates, and securely connect a client to a server using HTTPS.

### Key Features:
- Private Certificate Authority (CA): Setting up a CA to issue certificates for secure communication.
- Client Authentication: A client is issued a certificate and securely connects to the server using HTTPS.
- Testing: The secure client-server connection is verified using curl commands.

### Tools Used:
- SmallStep: Tool for managing certificates and PKI.
- Curl: For testing client-server connections over HTTPS.

### Objective:
The project aims to provide hands-on experience with PKI concepts, including creating and managing certificates and establishing secure communication using public key cryptography.

---

## Table of Contents

- [Step 1: Installing Step CLI](#step-1-installing-stepcli)
- [Step 2: Initializing the CA](#step-2-initializing-the-ca)
- [Step 3: Launching CA](#step-3-launching-ca)
- [Step 4: Creating Client Certificates and Inspecting](#step-4-creating-client-certificates-and-inspecting)
- [Step 5: Regenerating Certificates with Extended Expiry](#step-5-regenerating-certificates-with-extended-expiry)
- [Step 6: Server Code](#step-6-server-code)
- [Step 7: Conclusion](#step-7-conclusion)


---

## **Step 1: Installing Step CLI
To install SmallStep CLI on macOS, run the following commands:

```bash
brew install step
step version
```
![Installing Step CLI](./screenshots/Screenshot_at_May_25 21-29-38.png) 
## Step 2: Initializing the CA
Now, initialize the Certificate Authority (CA) with the following command:
```bash
step ca init
```
## Step 3: Launching CA
Launch the CA using this command:
```bash
step-ca $(step path)/config/ca.json
```

## Step 4: Generating a client certificate and checking it 
To generate a client certificate and inspect its details, use these commands:
```bash
step ca certificate "client.local" client.crt client.key 

step certificate inspect client.crt 
```

## Step 5: Regenerating certificates with bigger expiring time and launching https server with this certificates
To regenerate the certificate with an extended expiry time (e.g., 23 hours), run:
```bash
step ca certificate "client.local" client.crt client.key \
--not-after=23h
```

## Step 6: Server Code
Create a simple HTTPS server using the generated client certificates. 
```bash
const https = require("https");
const fs = require("fs");
const options = {
 key: fs.readFileSync("client.key"),
 cert: fs.readFileSync("client.crt"),
 ca: fs.readFileSync("chain.pem"),
};
https
 .createServer(options, (req, res) => {
 res.writeHead(200);
 res.end("Secure connection established via PKI!\n");
 })
 .listen(8080, () => {
 console.log("HTTPS server running at https://localhost");
 });

```


## Step 7: Conclusion

• The project successfully implements:
• Local Certificate Authority
• Certificate issuance and verification
• Client connection
• Application in HTTPS server
