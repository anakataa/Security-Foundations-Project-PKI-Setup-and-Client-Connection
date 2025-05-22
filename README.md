# Security Foundations Project: PKI Setup and Client Connection

Student: Staroshchuk Kirill(anakata) 

Course: Security Foundations  
Professor: Maksymilian Marcinkowski  
Date: May 22, 2025

---

## Project Overview

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

- [Step 1: Installing SmallStep](#step-1-installing-smallstep)
- [Step 2: Initializing the CA](#step-2-initializing-the-ca)
- [Step 3: Creating Client Certificates](#step-3-creating-client-certificates)
- [Step 4: Connecting the Client](#step-4-connecting-the-client)
- [Step 5: Testing](#step-5-testing)
- [Issues and Solutions](#issues-and-solutions)
- [Conclusion](#conclusion)
- [Tools and Versions Used](#tools-and-versions-used)
- [Appendices](#appendices)

---

## Step 1: Installing SmallStep

To begin the project, we first need to install SmallStep CLI. Run the following commands to install it on your local machine:

```bash
curl -sSL https://github.com/smallstep/cli/releases/download/v0.15.5/step-cli_0.15.5_amd64.deb -o step-cli_0.15.5_amd64.deb
sudo dpkg -i step-cli_0.15.5_amd64.deb
