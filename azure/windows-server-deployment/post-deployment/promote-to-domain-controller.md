# Domain Controller Promotion

## Objective
Domain Controller is the controller that manages all the users/groups/computers access, permissions on the network. The purpose of this lab is to turn the Windows server into a Domain Controller with Active Directory.<br>
In this lab, I will:<br>

- Promoting Domain Controller
- Creating a domain 
- Verify everything is setup correctly.

## Prerequisites
1. Have your Windows Server hosted on Microsoft Azure cloud
2. Roles and Features are fully installed on Windows Server
- Active Directory Domain Services
- DHCP Servers
- DNS Servers
- Print and Document Services
- Web Server (IIS)

<br>Refer to: [Window Server 2025 Deployment](/azure/windows-server-deployment/README.md)

## Steps
## Step 1: Access All Servers Task Details and Notifications
- On your server manager go to AD DS tab and click on 'more...' at "Configuration required for Active Directory Domain Systems at 'your domain name'"
<img src="screenshots/01- Server Manager AD DS.png" alt="Server Manager ADS tab" width="650">

## Step 2: Promote the server to a domain controller
- On the task, under Actions, click on 'Promote this server to a domain controller'.
<img src="screenshots/02-Promote server to DC.png" alt="Promote Server to a DC" width="650">

## Step 3: Deployment Configuration
- Add a new forest and 'lab.local' for your Root Domain name in Deployment Configuration tab
- Create Password for DSRM in the Domain Controller Options tab
- At the Prerequisites Check tab, install the necessary prerequisites and it will restart after successful installation.

## Step 4: Deployment Configuration
- Search Active Directory Users and Computers in the search bar
<img src="screenshots/03- Active Directory Users and Computers.png" alt="Active Directory Users and Computers" width="650">

- Forest: is your domain
- Organizational Units (OU) for your folders

## Step 5: Create Users, Groups, and Computers OU
- Right click on your domain -> new -> Organizational Unit and name your branch
- Right click on the OU you just created add new -> Organizational unit and name it 'Users'
- Do that same one for 'Groups' and 'Computers'
<img src="screenshots/04 - Forest of OUs.png" alt="Forest of OUs" width="650">

## Step 6: Add a User in the User OU
- Right click on Users -> New -> User
- Add First and Last name and User logon name as firstname.lastname format.
- Click 'next' and create a password and 'finish'
<img src="screenshots/05-User created.png" alt="Create a user inside User OU" width="650">

## Notes
- The AD Users and Computers has Forests and OUs of objects.