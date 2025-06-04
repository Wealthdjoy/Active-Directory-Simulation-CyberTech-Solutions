
# Active Directory Simulation – CyberTech Solutions

This project is the deployment of a Windows Server Domain Controller (Active Directory) for a company called **CyberTech Solutions**. It includes domain setup, client configuration, OU design, group policies, and access control in an enterprise environment.

---

## Company Structure

**CyberTech Solutions** is a small IT services firm with the following structure:

- 1 x Windows Server (AD Domain Controller)
- 1 x Windows 8 Client PC (HR Department)
- 1 x Windows 7 Client PC (Legacy Software)

---

## Project Objectives

- Configure an AD Domain Controller on Windows Server
- Join client PCs to the domain
- Create Organizational Units (OUs)
- Implement basic Group Policies for access control
- Simulate a centralized IT environment

---

## Network Design

```
Internet
   ↓
Router (Gateway: 10.0.5.1)
   ↓
Switch
 ┌──────┬─────────────┬──────────────┐
 │      │             │              │   
Server  PC1 (Win 8)   PC2 (Win 7)
```

| Device        | IP Address      | Role                        |
|---------------|----------------|-----------------------------|
| Windows Server| 10.0.5.5  | AD Domain Controller (DC)   |
| Windows 8 PC  | DHCP    | Client (Accounts)           |
| Windows 7 PC  | DHCP    | Legacy Client               |

---

## Domain Configuration

- **Domain Name**: `cybertech.local`
- **Server Name**: `CYBERTECH`
- **Static IP**: `10.0.5.5`
- **AD Roles Installed**: AD DS, DNS (DHCP)

---

## Organizational Units (OUs)

Created using **Active Directory Users and Computers**:

```
CyberTech.local
├── OU: IT Department
│   └── Users: Dee.IT


├── OU: HR
│   └── Users: Dove.HR
```

---

## Group Policy (GPO)

Created and linked using **Group Policy Management Console (gpmc.msc)**:

- **GPO 1**: `DisableRemovableDrives`
- **Linked to**: OU: HR and IT Department
- **Policy Configured**:
  - `Computer Configuration` > `Administrative Templates` > `System` > `Removable Storage Access`
  - Set **"All Removable Storage classes: Deny all access"** to **Enabled**

Result: USB and external drives are disabled for all users in the **HR and IT OU**.

- **GPO 2**: `DisablePowerOffRestartOption`
- **Linked to**: OU: HR and IT Department
- **Policy Configured**:
  - `Computer Configuration` > `Administrative Templates` > `System` > `Removable Storage Access`
  - Set **"Remove and prevent all access to shutdown, restart and hibernate commands"** to **Enabled**

Result: Commands disabled for all users in the **HR and IT OU**.


---

## Screenshots

- [AD Domain Structure](https://github.com/Wealthdjoy/Active-Directory-Simulation-CyberTech-Solutions/blob/main/Screenshots/OUs_Groups_and_Users.PNG)
- [GPO Editor Screenshot](https://github.com/Wealthdjoy/Active-Directory-Simulation-CyberTech-Solutions/blob/main/Screenshots/Group_policy_management.PNG)
- [Windows 7-PC joined to domain](https://github.com/Wealthdjoy/Active-Directory-Simulation-CyberTech-Solutions/blob/main/Screenshots/Windows_7_machine_configuration.PNG)
- [Windows 8-PC joined to domain](https://github.com/Wealthdjoy/Active-Directory-Simulation-CyberTech-Solutions/blob/main/Screenshots/Windows_8_machine%20_configuration.PNG)
- [Result of denied shutdown command access on Windows 7](https://github.com/Wealthdjoy/Active-Directory-Simulation-CyberTech-Solutions/blob/main/Screenshots/Windows_7_Alt_F4_access_denied.PNG)
- [Result of denied shutdown command access on Windows 8](https://github.com/Wealthdjoy/Active-Directory-Simulation-CyberTech-Solutions/blob/main/Screenshots/Windows_8_Alt_F4_access_denied.PNG)
- [Result of denied PowerOffRestartSleep option on Windows 7](https://github.com/Wealthdjoy/Active-Directory-Simulation-CyberTech-Solutions/blob/main/Screenshots/PowerOff_Restart_and_Sleep_access_denied_2.PNG)
- [Result of denied PowerOffRestartSleep option on Windows 8](https://github.com/Wealthdjoy/Active-Directory-Simulation-CyberTech-Solutions/blob/main/Screenshots/PowerOff_Restart_and_Sleep_access_denied_1.PNG)

---

## Key Takeaways

- Gained practical experience with Windows Server roles and domain setup
- Implemented centralized access control using Group Policy
- Learned how to structure users and departments with OUs
- Applied IAM concepts in a real-world simulated environment

---

## Author

**Dayo Sonibare**  
Cybersecurity Analyst  
