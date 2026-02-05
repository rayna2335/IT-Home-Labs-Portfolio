# Domain Controller Promotion

## Objective
A Domain Controller (DC) manages authentication, authorization, and directory services for users, groups, and computers within a Windows domain. The purpose of this lab is to promote a Windows Server to a Domain Controller by installing and configuring Active Directory Domain Services (AD DS).<br>

In this lab, I will:<br>

- Promote a Windows Server to a domain controller
- Create a domain name
- Add forests and OUs
- Verify the steps

## Prerequisites
1. Have Windows Server hosted on Microsoft Azure cloud
2. Roles and Features are installed on Windows Server.<br>

    Those are:
- Active Directory Domain Services (AD DS)
- DNS Servers
- DHCP Servers (Used in future lab)
- Print and Document Services (Used in future lab)
- Web Server (IIS) (Used in future lab)

\* For DC promotion, only AD DS and DNS Servers are required.

<br>Refer to: [Windows Server 2025 Deployment](/azure/windows-server-deployment/README.md)

## Steps
### Step 1: Access All Servers Task Details and Notifications
- On the Server Manager, go to the 'AD DS' tab on the left and click on 'More..' that says "Configuration required for Active Directory Domain Services at 'your domain name'"
<img src="screenshots/01- Server Manager AD DS.png" alt="Server Manager ADS tab" width="650">

### Step 2: Promote the Windows server to a domain controller
- Click on 'Promote this server to a domain controller' under the Action column.
<img src="screenshots/02-Promote server to DC.png" alt="Promote Server to a DC" width="650">

### Step 3: Deployment Configuration
- Select 'Add a new forest.' 
- Enter the Root domain name, such as `lab.local`, for homelab purposes

    \* Use other name in real settings as 'lab.local' will cause an issue with DNS.

- Create a password for Directory Services Restore Mode (DSRM) in the Domain Controller Options tab.

- At the 'Prerequisites Check' tab, install the necessary prerequisites, and the system will restart after a successful installation.

### Step 4: Verify Active Directory Installation
- Search 'Active Directory Users and Computers' in the search bar and click on it.
<img src="screenshots/03- Active Directory Users and Computers.png" alt="Active Directory Users and Computers" width="650">

    \* Forest, and Organizational Unit (OU) is populated under your root domain name that you created in Step 3.

### Step 5: Create Users, Groups, and Computers OU
- Right click on your root domain name -> New -> Organizational Unit and name your branch. 
    - Example name: `Branch1`
- Right click on the OU you just created, add new -> Organizational unit, and name it 'Users.'
- Repeat the process to add 'Groups' and 'Computers' under your branch.
<img src="screenshots/04 - Forest of OUs.png" alt="Forest of OUs" width="650">

### Step 6: Add a User in the User OU
- Right click on Users you just created -> click New -> User
- Add first, last name, and User logon name in this format: `firstname.lastname`
- Click ‘next’, and ‘finish.’
<img src="screenshots/05-User created.png" alt="Create a user inside User OU" width="650">
*The user was successfully created under the Users OU*

## Notes
- Domain Controllers have a writable copy of the Active Directory database, which allows any changes made to users, groups, or computures are automatically updates accross devices.
- A Forest represents a top level Active Directory and defines domain name spaces.