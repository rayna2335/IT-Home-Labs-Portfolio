# Active Directory User and Group Management

## Objective


## Prerequisites
1. Have Windows Server hosted on Microsoft Azure cloud
2. Roles and Features are installed on Windows Server
    - Refer to: [Windows Server 2025 Deployment](/azure/windows-server-deployment/README.md) 

3. Promote Windows server to Domain Controller 
    - Refer to: [Domain Controller Promotion](/azure/windows-server-deployment/post-deployment/domain-controller-promotion/promote-to-domain-controller.md)


## Steps

### Step 1: Open Active Directory Users and Computers (ADUC)
- Search for "Active Directory Users and Computers" from the Start menu

### Step 2: Create a User Account
- Right click the **Users** container → New → User
- Enter the user's first name, last name, and logon name
<img src="screenshots/01 - Add users.png" alt="Add users to domain" width="650">

*Note: If multiple users require identical permissions, an existing user account can be copied and renamed to maintain consistency.*

### Step 3: Create a Security Group
- Right click the **Users** container → New → Group
- Specify:
  - Group scope: **Global**
  - Group type: **Security**
<img src="screenshots/02 - Add users to a group.png" alt="Added Users to a group" width="650">

### Step 4: Add Users to the Group
- Open the group → Members tab → Add users


## Notes
- User account management tasks such as password resets, account unlocks, and account disablement are commonly performed through ADUC.
- Best practice is to assign permissions to **groups**, not individual users, and then add users to the appropriate groups.
- This approach simplifies permission management and improves security and scalability.
