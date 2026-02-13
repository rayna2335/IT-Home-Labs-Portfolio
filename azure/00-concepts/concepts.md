# Home Lab Concept Dictionary
___

### 🔸 Active Directory

#### Definition: 
#### Purpose:
#### How it works:
#### How I applied it in the Lab:
- Created Organizational Unit (OU) to seporate
- Created Users and groups inside the OU
#### Troubleshooting insights (Tips):
___
---
### 🔸 Domain Controller (DC)

**What is it?** A server running Active Directory, implemented to centrally authenticate and manage users within a domain. Important note: Active Directory (AD) is the overall system, while Active Directory Domain Services (AD DS) is a specific server role. A server only becomes a Domain Controller onces it has been promoted with AD DS role.

<p align="center">
  <img src="screenshots/01-domain-controller.png" 
       alt="Domain Controller Architecture" 
       width="250"><br>
  <em>Figure 1: Domain Controller Architecture Overview</em>
</p>

**What does it do?**  
- Authenticate the identity of users and computers
- Authorize access, permissions to resources inside a domain

**Lab Implementation (My experience)**: In my Microsoft Azure homelab, I deployed a Windows Server 2025 image and promoted to a DC. By installing and configuring AD DS, I created a centralized management for the madeup users and endpoints in my virtual network.

#### Troubleshooting insights (Tips): 

---
## 🔸 Registery

### Definition:
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

---
## 🔸 Default Domain Policy

### Definition:
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

---
## 🔸 Group Policy Management Editor

### Definition:
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

---
## 🔸 Policies vs Preferences

### Definition:
- Policies: Users does not have the right to change any options. Implemented with the registery.

- Preferences: Users can decide its own rules to set. The original preference setting will default after each start up.
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

---
## 🔸 Computer Configuration

### Definition:
### Purpose:
### How it works:
- Settings applies to the computer itself, and configure how the machines should behave.
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

---
## 🔸 User Configuration

### Definition:
### Purpose:
### How it works:
- Setting applies to the user, no matter what computer they log into.
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

___
## 🔸 VNet

### Definition:
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

___
## 🔸 Subnet

### Definition:
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

___
## 🔸 Ethernet Connctor

### Definition:
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

___
## 🔸 Domain Credentials

### Definition:
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

___
## 🔸 Local Credentials

### Definition:
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

___
## 🔸 

### Definition:
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):
___
## 🔸 Local Credentials

### Definition:
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

___
## 🔸 Server Manager

### Definition:
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

___
## 🔸 DHCP

### Definition:
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

___
## 🔸 DNS

### Definition:
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

___
## 🔸 Organizational Unit

### Definition:
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):


___
## 🔸 Root Domain Name

### Definition:
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

___
## 🔸 Forest

### Definition:
### Purpose:
### How it works:
### How I applied it in the Lab:
### Troubleshooting insights (Tips):

