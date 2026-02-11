# Join a PC client to AD domain 

## Objective
The purpose of this lab is to join a PC to domain, <br>

## Prerequisites
1. Have Windows Server hosted on Microsoft Azure cloud
2. Roles and Features are installed on Windows Server
    - Refer to: [Windows Server 2025 Deployment](/azure/windows-server-deployment/01-initial-deployment/windows-server-deployment.md) 

3. Promote Windows Server to Domain Controller 
    - Refer to: [Domain Controller Promotion](/azure/windows-server-deployment/02-domain-controller/promote-to-domain-controller.md)


## Steps

### Step 1: Create a Virtual PC
- Follow the same set up in: [Windows Server 2025 Deployment](/azure/windows-server-deployment/01-initial-deployment/windows-server-deployment.md) and name the VM. (this will be the workgroup)

- Check Subnet by going on **Networking** tab and under **subnet** you can set the same subnet range as your DC subnet.

- Go to 'Network settings' and click on your NIC.
- Check Your Private IP address and it should be in the same range as the subnet for DC

*Note: in Microsoft Azure use the Windows Server 2025 Datacenter image since the Windows 11 Pro require to to have your own license*

*Note: This PC should be in the same subnet as your DC (Important!)*


### Step 2: Resolve this PC to our domain name 
- On your PC VM, go to DNS servers under Settings.
- Click **Custom**

*Note: Since this is on a Virtual machine and not on a actual enterprise enviroment, we would need to configure the DNS server to our Domain Controller*


### Step 3: Connect via Bastion for your PC

### Step 4: 
- Go to Settings from the Start menu
- Systems -> About -> Advaneced systems settings -> Computer Name 
    - The device is initially set to WORKGROUP
- Click 'Change..' to put this PC on the DC
- Click Member of Domain option and enter the same domain name from: [Domain Controller Promotion](/azure/windows-server-deployment/02-domain-controller/promote-to-domain-controller.md) which in this case was **lab.local**
- enterthe domain username and password.
- It will restart your computer right after successful joining.


### Troubleshooting:
- "AD DC for the domain could nto be contacted" which means that DNS is not able to reach the domain
1. in the search bar type: **ncpa.cpl** for Ethernet Connector
2. Right click and go to properties
3. Right click on IPv4
4. On a seporate tab, open Command Prompt
5. **ipconfig /all** to see your DNS Server IP and if this address doesnt match up to your DC IP, go back to step 2 and enter your DC IP and click "ok"








## Notes