# Domain Controller Promotion

## Objective
A Domain Controller (DC) manages authentication, authorization, and directory services for users, groups, and computers within a Windows domain. The purpose of this lab is to promote a Windows Server to a Domain Controller by installing and configuring Active Directory Domain Services (AD DS).<br>

In this lab, I will:<br>

- Promote a Windows Server to a DC
- Create a domain name
- Add forests and OUs
- Verify the steps

## Prerequisites
1. Have Windows Server hosted on Microsoft Azure cloud
2. Roles and Features are installed on Windows Server.<br>

    Those are:
- Active Directory Domain Services (AD DS)
- DNS Servers

\* For DC promotion, only AD DS and DNS Servers are required.

<br>Refer to: [Windows Server 2025 Deployment][wsd]

## Network Diagram

<p align="center">
  <img src="screenshots/00-domain-architecture.png" 
       alt="Domain Architecture" 
       width="350"><br>
  <em>Figure 2: Domain Architecture Overview</em>
</p>

## Steps
### Step 1: Access All Servers Task Details and Notifications
- On the Server Manager, go to the 'AD DS' tab on the left and click on 'More..'
<img src="screenshots/01-server-manager-ad-ds.png" alt="Server Manager AD DS tab" width="650">

### Step 2: Promote the Windows server to a domain controller
- Click on 'Promote this server to a domain controller' under the Action column.

### Step 3: Deployment Configuration
- Select **Add a new forest** 
- Enter the **Root domain name** following this convention (____.local)

- Create a password for Directory Services Restore Mode (DSRM) in the Domain Controller Options tab.

- At the **Prerequisites Check** tab, install the necessary prerequisites, and the system will restart after a successful installation.

### Step 4: Verify Active Directory Installation
- Search for 'Active Directory Users and Computers' in the search bar and verify that the domain you created are visible.
<img src="screenshots/03-active-directoroy-users-computers-verify-domain-creation 2.png" alt="Active Directory Users and Computers" width="650">

    \* Organizational Unit (OU) is populated under your root domain name that you created in Step 3.

### Step 5: Create Users, Groups, and Computers OU
- Right click on your **root domain name** -> **New** -> **Organizational Unit** and name your branch. 
- Right click on the OU you just created, add new -> OU, and name it 'Users.'
- Repeat the process to add 'Groups' and 'Computers' under your branch.
<img src="screenshots/04-create-ou-user-group-computer.png" alt="New OU with Users, Groups, Computers" width="650">

### Step 6: Add a User in the User OU
- Right click on **Users** you just created -> click **New** -> **User**
- Enter first, last name, and User logon name in this format: `firstInitial.lastname`
- Click **next**, and create an password and click **finish**.
<img src="screenshots/05-create-user.png" alt="Create a user inside User OU" width="650">

*A user successfully created under the Users OU*

## Notes
- Domain Controllers have a writable copy of the Active Directory database, which allows any changes made to users, groups, or computures are automatically updates accross devices.


## Concepts used:
[Active Directory](../../00-concepts/concepts.md#🔸-active-directory)

[Domain Controller](../../00-concepts/concepts.md#🔸-domain-controller-dc)

[Organizational Unit](../../00-concepts/concepts.md#🔸-organizational-unit)

[Root Domain Name](../../00-concepts/concepts.md#🔸-root-domain-name)


[wsd]: /azure/windows-server-deployment/01-initial-deployment/windows-server-deployment.md