# Join a PC client to AD domain 

## Objective
The purpose of this lab is to understand how to domain join a PC and verify that a PC is connected to the DC. <br>

## How Domain Join Works (Concept)
- Network connectivit to the DC
- DNS resolution to DC
- Proper credentials 

## Architecture

## Prerequisites
1. Have Windows Server hosted on Microsoft Azure cloud
2. Roles and Features are installed on Windows Server
    - Refer to: [Windows Server 2025 Deployment][wsd]
3. Promote Windows Server to Domain Controller 
    - Refer to: [Domain Controller Promotion][dcp]


## Steps

### Step 1: Create a Virtual PC
*Note: In Microsoft Azure, use the Windows Server 2025 Datacenter image since the Windows 11 Pro requires a license*

- Follow the same setup in: [Windows Server 2025 Deployment][wsd] and name the VM.

- Check Virtual Network (VNet) by going to the **Networking** tab.
- Set **VNet** same as your DC.
- Go to **Network settings** and click on your NIC.

<img src="screenshots/01-check-vnet-and-subnet.png" alt="Match VNet and subnet to DC" width="650">

*PC's IP Configuration*

<img src="screenshots/04-dc-ip-settings.png" alt="DC IP settings" width="650">

*DC's IP Configuration*

*Note: This PC should be in the same Virtual Network (VNet) as DC. Being in the same subnet simplifies configuration but not strictly required*


### Step 2: Resolve this PC to domain name 
- On the PC, go to **DNS servers** under Settings.
- Click **Custom**
- (IMPORTANT!) The client must use the DC's private IP address as its primary DNS Server

*Note: Since this is on a Virtual machine and not on a actual enterprise enviroment, we would need to manually configure the DNS server to our Domain Controller*

### Step 3: Connect via Bastion for your PC

### Step 4: Connect Domain to PC
- Go to Settings from the Start menu
- Systems -> About -> Advanced Systems Settings 
- Go to **Computer Name** tab
- The device is initially set to WORKGROUP
- Click 'Change..' to join this PC to the DC
- Click **Member of Domain** option and enter the same domain name from: [Domain Controller Promotion][dcp] (In this case: **lab.local**)

<img src="screenshots/02-add-domain-name-as-a-member-of-this-pc.png" alt="Add domain name as a member of this PC" width="650">

*Note: There may be an troubleshooting step here because Bastion sometimes does not update the DNS, so we would need to manually input the DNS IP address. See Troubleshooting steps for more information.*

- Enter the domain username and password.

<img src="screenshots/06-Connect to your DC.png" alt="Connect to DC computer" width="650">

- Will see a message confirming the domain was successufly joined. The computer will restart after successful joining.

<img src="screenshots/07-access-to-your-dc.png" alt="Success message of accesss DC" width="350">

### Troubleshooting:
<img src="screenshots/03-troubleshooting.png" alt="Could not be contacted error" width="450">

- If you see an error:
    - "AD DC for the domain could not be contacted" which means DNS was not able to reach the domain so make sure that your newly created PC is in the same subnet and Virtual network (VNet) as your DC

Steps to fix: 
1. In the search bar, type: **ncpa.cpl** to open Ethernet Connector
2. Right click on Ethernet adapter and go to **Properties**
3. Click on IPv4, and go to **Properties**

4. Then, on a seporate tab, open Command Prompt
5. Run: **ipconfig /all** 
    - To check the DNS Server IP 
    - If it does not match your DC's IP address, go back to IPv4 setting and manually enter your DC's IP address. Click **Ok** 

<img src="screenshots/05-troubleshooting-match-DNS-to-DC IP.png" alt="Match DNS to DCs" width="650">

### Step 5: Verify that the PC is Connected to the DC
- Open Command Prompt on the PC
- Ping the domain name:
    - **ping lab-dc** to test hostname resolution

    <img src="screenshots/08-check-for-connectivity-on-dc-from-pc.png" alt="Check for connctivity on DC from PC" width="650">

- If success you will recieve connection replies and if not, the request will time out.

- Go on your DC VM and go to **Active Directory Users and Computers**. Under **Computers**, the newly created PC should appear.
- Move the new PC to the correct OU by dragging it to the branch you created called Computers.

<img src="screenshots/09-join-computer-to-domain.png" alt="Propagated PC on DC" width="650">

### Step 6: Commands to see User Accounts
- Run **net user** to see what user is on the system

<img src="screenshots/10-net-user.png" alt="Net user command" width="650"> 

- Run **net localgroup administrators** to see who is the member of the Administrators group.

<img src="screenshots/12-net-localgroup-admin.png" alt="Command to view who is in the member in the Admin group" width="650">

Another way to check:
    - Search for **Local Users and Groups** in the search bar
    - Click on **Groups** -> **Administrators**
    - View the members of the Administrators group.

<img src="screenshots/11-Admin group.png" alt="View who is in the member in the Admin group" width="650">

### Steps 7: Delete Admin User and Group
- After creating temperary administrator user and group, delete them using:
    - To remove a local user: **net user username /delete**
    - To remove user from admin group: **net localgroup administrators default /delete**


## Notes:
- Joining a domain only works for windows version Pro/Enterprise. Windows home version does not have the functionally to join the server.


## Concepts used:
[Domain Controller](../../../00-concepts/concepts.md#🔸-domain-controller-dc)

[VNet](../../../00-concepts/concepts.md#🔸-vnet)

[Subnet](../../../00-concepts/concepts.md#🔸-subnet)

[Ethernet Connctor](../../../00-concepts/concepts.md#🔸-ethernet-connctor)

[Domain Credentials](../../../00-concepts/concepts.md#🔸-domain-credentials)

[Local Credentials](../../../00-concepts/concepts.md#🔸-local-credentials)




[wsd]: /azure/windows-server-deployment/01-initial-deployment/windows-server-deployment.md

[dcp]: /azure/windows-server-deployment/02-domain-controller/promote-to-domain-controller.md

[ugm]: /azure/windows-server-deployment/03-active-directory/01-user-and-group-management/create-users-and-groups.md