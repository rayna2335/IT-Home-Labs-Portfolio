# Windows Server 2025 Deployment on Microsoft Azure
**Platform:** Microsoft Azure 
<br>
**Status:** In progress

---

## Objective
Deploy and configure a Windows Server 2025 virtual machine in Microsoft Azure to gain hands-on experience with cloud, networking ,and basic server administration. We will also install Active Directory Domain Services, DHCP Server, DNS Server, Group Policy Management, Print and Document Services, and Web Server (IIS). 

## Lab Environment
**Cloud Platform:** Microsoft Azure

**Operating System:** Windows Server 2025

## Prerequisites
- Create an account on Microsoft Azure

## Architecture Overview

# Steps
### Step 1: Create a Microsoft Azure account
<img src="screenshots/01-dashboard.png" alt="Account created" width="650" />

### Step 2: Create a Virtual Machine
Click on 'create a resource' and click on 'Create' for the Virtual machine option.
### Step 3: Configure the Virtual machine
<img src="screenshots/02-virtual%20machine%20review.png" alt="VM review" width="650" />

Subscription: Azure Subscription 1<br>
Resource Group: name your Window server (Purpose is to keep all resources together)<br>
Virtual machine name: Name your VM<br>
Region: Enter your location <br>
Availability options: Availability zone<br>
Zone option: Self-selected zone<br>
Availablity zone: Zone 3<br>
Security type: Trusted launch virtual machines<br>
Image: Windows Server 2025 Datacenter: Azure Edition - x64 Gen2<br>
Size: Standard_E2s_v3 - 2 vcpus, 16 GiB memory ($181.04)<br>
Username: enter any username<br>
Password: enter any password<br>
Inbound ports: None
### Step 4: Wait for deployment to complete processing
### Step 5: Set static IP for Domain Controller (DC)
on the side bar go to **networking** and **network settings**. Click on your network interface. Click on your IP config and set the private IP address settings to static.
### Step 6: Connect to your VM
<img src="screenshots/03-Connect VM.png" alt="Connect VM" width="650" />

Search your VM name and click on **Connect**, and **connect via Bastion**
Enter your Username and password to connect.
### Step 7: Configure Server Manager to stop automatically showing after logon
Go to Manage, properties, and then check mark ‘do not start Server Manager automatically at logon.
### Step 8: Install roles and features
<img src="screenshots/04-Install%20Roles%20and%20features.png" alt="Install roles and features" width="650" />

Click manage -> Add Roles and Features -> and add the roles and feaures in the Server Roles. (Active Directory Domain Services, DHCP Servers, DNS Servers, Print and Document Services, Web Server (IIS)). And let the system install its roles and features.
### Step 9: Restart your Windows Server
### Step 10: Log back into your Window Server
Fully functional Windows Server instance with roles and features all set up.



# Issues/Troubleshooting
To ensure you keep your costs low, make sure to deallocate your VM after each use. OR you can delete the resource group to keep it at no cost.

# What I Learned

# References
