---
title: Windows Server 2025 Administration
description: 
published: true
date: 2025-05-18T22:03:41.200Z
tags: windows server
editor: markdown
dateCreated: 2025-05-16T10:33:58.170Z
---



## Contents
- [Overview](#Overview-1)
- [Installation & Configuration](#Installation-&-Configuration-2)
- [Active Directory AD DS](#Active-Directory-AD-DS-3)
- [Networking Services](#Networking-Services-4)
- [File and Storage Services](#File-and-Storage-Services-5)
  - [Configure iSCSI Storage with MPIO](#Configure-iSCSI-Storage-with-MPIO)
- [Server Security](#Server-Security-6)
- [Server Virtualization and Containers](#Server-Virtualization-and-Containers-7)
- [Automation and Scripting](#Automation-and-Scripting-8)
- [Backup and Disaster Recovery](#Backup-and-Disaster-Recovery-9)
- [Monitoring and Performance](#Monitoring-and-Performance-10)
- [Troubleshooting and Mainteance](#Troubleshooting-and-Maintenance-11)


## Overview
- What is Windows Server 2025

> Windows Server 2025 is the latest version of Microsoft's server operating system, officially released on November 1, 20-24.  It builds on previous versions with enhanced security, improved performance, and better cloud integration.
{.is-info}

[Windows Server 2025](https://www.microsoft.com/en-us/windows-server/blog/2024/11/04/windows-server-2025-now-generally-available-with-advanced-security-improved-performance-and-cloud-agility/)

- New Features and enhancements

    - **Advanced Security: Includes Active Directory Improvements, SMB over QUIC, and Delegate Managed Service Accounts (dMSA) for better authentication.**
    - **Hybrid Cloud Capabilities: Supports hotpatching via Azure Arc, reducing downtime for security updates.**
    - **Performance Enhancements:  Faster storage options, file compression, and Bluetooth support.**
    - **Updated User Experience:  Features a Windows 11-style desktop, Wi-FI support, and modern Task Manager.**
    - **System Requirements: Requires a 1.4 GHz 64-bit processor, 512 MB RAM (Server Core) or 2 GB RAM (Desktop Experience), and at least 32 GB storage.**
    - **Windows Server 2025 is designed for on-premised, hybrid, and cloud environments**

- Server roles and editions
## Installation & Configuration
- System requirements and hardware planning
- Installation options (GUI, Core, Nano)
- Post-installation configuration
- Licensing and activation
## Active Directory (AD DS)
- Introduction to AD DS
- Installing and Configuring Domain Controllers
- Managing users, groups, and organizational units (OUs)
- Group Policy Basics and Management
## Networking Services
- IP Addressing and DHCP

> **IPv4 Addressing consists of a Total of 32 Bits/4 Octets, 8 Bits/Octect**
>    **(Reference IETF RFC 791)**
> 
>     IPv4 Classes   IPv4 Range             IPv4 Subnetting
>           A    →     1-127                   255.0.0.0
>           B    →     128-191                 255.255.0.0
>           C    →     192-223                 255.255.255.0
>           D    →     224-239
>           E    →     240-255













- DNS server setup and management
- Network policy and access services (NPS)
- Remote Access (VPN, Direct Access)
## File and Storage Services
- File Server roles and features
- NTFS and Permissions
- Distributed Files System (DFS)
- Storage Spaces and Disk Management
- Configure iSCSI Storage with MPIO
> iSCSI stands for Internet Small Computer System Interface.  iSCSI Storage is a way to share block-level storage over a standard IP Network. MPIO stands for Multipath I/O.  MPIO is a storage-fault-tolerance and load-balance feature that lets an operating system use two or more physical paths to reach the same block-storage device, in essence it offers redundancy.
{.is-info}

**Install iSCSI Feature**

1.  In Server Manager, select Manage menu and then select Add Roles and Features.
![slide_1.png](/configure-iscsi-storage/slide_1.png){.align-left}
2.  In the Add Roles and Features Wizard, on the Before you begin page, select Next.
![slide_2.png](/configure-iscsi-storage/slide_2.png){.align-left}
3. On the Select Installation type page, select Next. (Role-based or feature-based installation.
![slide_3.png](/configure-iscsi-storage/slide_3.png){.align-left}
4. On the Select destination server page, ensure that Select a server from the server pool is selected (Choose your Server), and then select Next.
![slide_4.png](/configure-iscsi-storage/slide_4.png){.align-left}
5. On the Select Server Roles page, expand File and Storage Services, then expand File and iSCSI Services, then select iSCSI Target Server and then select Next. Select Add Features. Select Next. This feature needs to be installed on both the Target and the Initiator.
![select_7.png](/configure-iscsi-storage/select_7.png){.align-left}
6.  On the Select Features page, select Next.
![slide_7.png](/configure-iscsi-storage/slide_7.png){.align-left}
7. On the Confirm installation selections page, select Install.
![slide_8.png](/configure-iscsi-storage/slide_8.png){.align-left}  
8. When the installation completes, select Close.
![slide_9.png](/configure-iscsi-storage/slide_9.png){.align-left}

**Create and Configure an iSCSI Target**

1.	In the Target Server Manager, in the navigation pane, select File and Storage Services.
![slide_10.png](/configure-iscsi-storage/slide_10.png){.align-left}
2.	In the File and Storage Services pane, select iSCSI. In the iSCI Virtual Disks pane, select Tasks, and then select New iSCSI Virtual Disk.
![slide_11.png](/configure-iscsi-storage/slide_11.png){.align-left}
3.	In the New iSCSI Virtual Disk Wizard, on the Select iSCSI Virtual Disk Location page, under Storage Location, select volume C: and then select Next.
![slide_12.png](/configure-iscsi-storage/slide_12.png){.align-left}
4.	On the Specify iSCSI Virtual Disk Name page, in the Name text box, enter iSCSI Disk1 and then select Next.
![slide_13.png](/configure-iscsi-storage/slide_13.png){.align-left}
5.	On the Specify iSCSI virtual disk page, in the Size text box, enter 5.  Ensure that GB is selected and then select Next.
![slide_14.png](/configure-iscsi-storage/slide_14.png){.align-left}
6.	On the Assign iSCSI Target page, ensure that the New iSCSI Target option is selected and then select Next.
![slide_15.png](/configure-iscsi-storage/slide_15.png){.align-left}
7.	On the Specify target name page, in the Name text box, enter your Server Name and the select Next.
![slide_16.png](/configure-iscsi-storage/slide_16.png){.align-left}
8.	On the Specify Access Servers page, select Add.
![slide_17.png](/configure-iscsi-storage/slide_17.png){.align-left}
9.	In the Select a method to identify the initiator dialog box, select Enter a value for the selected type.  In the Type list, select IP Address. In the Value text box enter 192.168.4.194 (Target’s IP) and then select ok.
![slide_18.png](/configure-iscsi-storage/slide_18.png){.align-left}
10.	On the Specify access servers page, select Next.
![slide_19.png](/configure-iscsi-storage/slide_19.png){.align-left}
11.	On the Enable Authentication page, select Next.
![slide_20.png](/configure-iscsi-storage/slide_20.png){.align-left}
12.	On the Confirm Selections page, select Create.
![slide_21.png](/configure-iscsi-storage/slide_21.png){.align-left}
13.	On the View Results page, wait until the Virtual disk is created, and then select Close.
![slide_22.png](/configure-iscsi-storage/slide_22.png){.align-left}
14.	In the iSCSI Virtual Disks pane, select Tasks and then select New iSCSI Virtual Disk.
![slide_23.png](/configure-iscsi-storage/slide_23.png){.align-left}
15.	In the New iSCSI Virtual Disk Wizard, on the Select iSCSI Virtual Disk Location page, under Storage location, select volume C: and then select Next.
![slide_24.png](/configure-iscsi-storage/slide_24.png){.align-left}
16.	On the Specify iSCSI Virtual Disk Name page, in the Name text box, enter iSCSIDisk2 and then select Next.
![slide_25.png](/configure-iscsi-storage/slide_25.png){.align-left}
17.	On the Specify iSCSI virtual disk size page in the Size text box, enter 5.  Ensure GB is selected and then select Next.
![slide_26.png](/configure-iscsi-storage/slide_26.png){.align-left}
18.	On the Assign iSCSI Target page, select cole-svr2 and then select Next.
![slide_27.png](/configure-iscsi-storage/slide_27.png){.align-left}
19.	On the Confirm selections page, select Create.
![slide_28.png](/configure-iscsi-storage/slide_28.png){.align-left}
20.	On the View results page, wait until the virtual disk is created and then select Close.
![slide_29.png](/configure-iscsi-storage/slide_29.png){.align-left}

**Configure MPIO**

1.	In Server Manager, select Manage menu, and then select Add Roles and Features.
![slide_30.png](/configure-iscsi-storage/slide_30.png){.align-left}
2.	In the Add Roles and Features Wizard, on the Before you begin page, select Next.
![slide_31.png](/configure-iscsi-storage/slide_31.png){.align-left}
3.	On the Select Installation Type, page select Next.
![slide_32.png](/configure-iscsi-storage/slide_32.png){.align-left}
4.	On the Select Destination Server page, ensure that Select a Server from the Server Pool is selected and then select Next.
![slide_33.png](/configure-iscsi-storage/slide_33.png){.align-left}
5.	On the Select Server Roles page, select Next.
![slide_34.png](/configure-iscsi-storage/slide_34.png){.align-left}
6.	On the Select Features page, select Multipath I/O and then select Next.
![slide_35.png](/configure-iscsi-storage/slide_35.png){.align-left}
7.	On the Confirm Installation selections page, select Install.
![slide_36.png](/configure-iscsi-storage/slide_36.png){.align-left}
8.	When the installation is complete, select Close.
![slide_37.png](/configure-iscsi-storage/slide_37.png){.align-left}
9.	Restart the Server.
10.	In Server Manager, select Tools and select iSCSI Initiator.
![slide_38.png](/configure-iscsi-storage/slide_38.png){.align-left}
11.	In the Microsoft iSCSI message box, select Yes.
![slide_39.png](/configure-iscsi-storage/slide_39.png){.align-left}
12.	In the iSCSI Initiator Properties dialog box, on the Targets Tab, in the Target text box, enter 192.168.4.194 (IP Address of your Target) and then select Quick Connect.
![slide_40.png](/configure-iscsi-storage/slide_40.png){.align-left}
13.	In the Quick Connect box, select Done.
![slide_41.png](/configure-iscsi-storage/slide_41.png){.align-left}
14.	In the iSCSI Initiator Properties dialog box, select Ok.
![slide_42.png](/configure-iscsi-storage/slide_42.png){.align-left}
15.	In the Server Manager, on the menu bar, select Tools, and then select MPIO.
![slide_43.png](/configure-iscsi-storage/slide_43.png){.align-left}
16.	In the MPIO Properties dialog box, on the Discover Multi-Paths Tab, select Add support for iSCSI devices and then select Add. Restart the Server. Select Ok at the message prompt and then select Ok to close the MPIO Properties.
![slide_44.png](/configure-iscsi-storage/slide_44.png){.align-left}
17.	In the Server Manager, on the menu bar, select Tools and then select MPIO.
![slide_45.png](/configure-iscsi-storage/slide_45.png){.align-left}
18.	In the MPIO Properties dialog box, on the MPIO Devices tab, notice that Devices Hardware ID has been added to the list.
![slide_46.png](/configure-iscsi-storage/slide_46.png){.align-left}
19.	In the MPIO Properties dialog box select Ok to close the dialog box.

**Connect to the iSCSI Target**

1.	On the client machine connecting to the Target machine, in the Server Manager, on the menu bar, select Tools and then select iSCSI Initiator.
![slide_47.png](/configure-iscsi-storage/slide_47.png){.align-left}
2.	In the iSCSI Initiator Properties dialog box, on the Targets tab, select Disconnect.
![slide_48.png](/configure-iscsi-storage/slide_48.png){.align-left}
3.	In the Disconnect From All Sessions dialog box, select Yes.
![slide_49.png](/configure-iscsi-storage/slide_49.png){.align-left}
4.	In the iSCSI Initiator Properties dialog box, on the Targets tab, select Connect.
![slide_50.png](/configure-iscsi-storage/slide_50.png){.align-left}
5.	In the Connect to Target dialog box, select the Enable multi-path checkbox.  Verify that the Add this connection to the list of Favorite Targets checkbox is selected, and then select Advanced.
![slide_50_(1).png](/configure-iscsi-storage/slide_50_(1).png){.align-left}
6.	In the Advanced Settings dialog box, on the General tab, changed the Local Adapter from Default to Microsoft iSCSI Initiator.
![slide_51_-_1.png](/configure-iscsi-storage/slide_51_-_1.png){.align-left}
7.	In the Initiator IP list, select your Initiator IP.
![slide_52_-1.png](/configure-iscsi-storage/slide_52_-1.png){.align-left}
8.	In the Target IP list, select your Target IP. In the Advanced Settings dialog box, select Ok.
![slide_53_-1.png](/configure-iscsi-storage/slide_53_-1.png){.align-left}	
9.	In the Connect to Target dialog box, select Ok.
![slide_54-1.png](/configure-iscsi-storage/slide_54-1.png){.align-left}
10.	In the ISCSI Initiator Properties dialog box, on the Targets tab, select Connect.
![slide_55.png](/configure-iscsi-storage/slide_55.png){.align-left}
11.	In the Connect to Target dialog box, select Enable multi-path.  Verify that the Add this connection to the list of Favorite Targets checkbox is selected, and then select Advanced.
![slide_50_(1).png](/configure-iscsi-storage/slide_50_(1).png){.align-left}
12.	In the Advanced Settings dialog box, on the General tab, changed the Local Adapter from Default to Microsoft iSCSI Initiator.
![slide_51_-_1.png](/configure-iscsi-storage/slide_51_-_1.png){.align-left}
13.	In the Initiator IP list, select your Initiator IP Address.
![slide_52_-1.png](/configure-iscsi-storage/slide_52_-1.png){.align-left}
14.	In the Target portal IP list, select your Target IP Address. In the Advanced Settings dialog box, select Ok.
![slide_53_-1.png](/configure-iscsi-storage/slide_53_-1.png){.align-left}
15.	In the Connect Target dialog box, select Ok.
16.	In the iSCSI Initiator Properties dialog box, on the Volumes and Devices tab, select Auto Configure.
17.	In the iSCSI Initiator Properties dialog box, on the Targets tab, in the Targets list, select your iqn and then select Devices.
![slide_61.png](/configure-iscsi-storage/slide_61.png){.align-left}
18.	In the Devices dialog box, select MPIO.
![slide_60.png](/configure-iscsi-storage/slide_60.png){.align-left}
19.	Verify that in the Load balance policy, Round Robin is selected.
![slide_59.png](/configure-iscsi-storage/slide_59.png){.align-left}
20.	Under this device has the following paths, notice that 2 paths are listed.  Select the first path and then select Details.
21.	Note the IP Address of the Source and Target portals and then select Ok.
22.	Select the second path and then select Details.
23.	Verify that this path is using another network and then select Ok.
24.	In the Device Details dialog box select Ok.
25.	In the Devices dialog box select Ok.
26.	In the iSCSI Initiator Properties dialog box select Ok.

**Initialize the iSCSI disks**

1.	On the Target Server, select File and Storage Services and then in the left pan select Disks.
![initialize_iscsi_disks.png](/configure-iscsi-storage/initialize_iscsi_disks.png){.align-left}
2.	In the iSCSI pane, right click or access the context menu for an offline disk with a bus type of iSCSI and then select Assign iSCSI Virtual Disk.
![initialize_iscsi_disks_-2.png](/configure-iscsi-storage/initialize_iscsi_disks_-2.png){.align-left}
3.	In the Assign iSCSI target pane, select Existing iSCSI target, and select Next. In the Confirm Selections pane, select Assign.
![initialize_iscsi_disks_-_3.png](/configure-iscsi-storage/initialize_iscsi_disks_-_3.png){.align-left}
4.	In the View results pane, select Close.
![initialize_iscsi_disks_-4.png](/configure-iscsi-storage/initialize_iscsi_disks_-4.png){.align-left}

**Configuring and managing the share infrastructure**

1.	On the Server with the Initiator, select File and Storage Services, and then select Shares.
![share_-_1.png](/share_-_1.png){.align-left}# Windows Server 2025
2.	In the Shares area, select Tasks and then select New Share.
![share_-2.png](/configure-iscsi-storage/share_-2.png){.align-left}
3.	In the New Share Wizard, on the Select the profile for this share page, in the File share profile box, select SMB Share – Quick and then select Next.
![share_-3_.png](/configure-iscsi-storage/share_-3_.png){.align-left}!
4.	On the Select the server and path for this share page, select the Initiator computer.  Select by volume, select the letter and then select Next.
[share_-_4.png](/configure-iscsi-storage/share_-_4.png){.align-left}!
5.	On the Specify share name page, in the Share name text box, enter Data and then select Next.
[share_5.png](/configure-iscsi-storage/share_5.png)
6.	On the Configure share settings page, select the Enable access-based enumeration checkbox, and then select Next.
![share_-_6.png](/configure-iscsi-storage/share_-_6.png){.align-left}!
7.	On the Specify permissions to control access page, select Customize permissions.
[share_-_7.png](/configure-iscsi-storage/share_-_7.png){.align-left}
8.	In the Advanced Security Settings for Data window, on the Permissions tab, select Add.
![share_-_8.png](/configure-iscsi-storage/share_-_8.png){.align-left}
9.	In the Permission Entry for Data window, select, Select a principal, enter Domain Users and then select Ok.
![share_-_9.png](/configure-iscsi-storage/share_-_9.png){.align-left}
10.	In the Basic permissions area, select Modify checkbox and then select Ok.
![share_-_10.png](/configure-iscsi-storage/share_-_10.png){.align-left}
11.	In the Advanced Security Settings for Data window select Ok.
![share_-_11.png](/configure-iscsi-storage/share_-_11.png){.align-left}
12.	On the Specify permissions to control access page, select Next.
![share_-_12.png](/configure-iscsi-storage/share_-_12.png){.align-left}
13.	On the Confirm selections page, select Create.
![share_-_13.png](/configure-iscsi-storage/share_-_13.png){.align-left}
14.	When the share creating is complete, select Close.

**Create an NFS Share on iSCSI Storage**

1.	On the Target Server, in the Shares area, select Tasks and then select New Share.
![nfs_share_-_1.png](/configure-iscsi-storage/nfs_share_-_1.png){.align-left}
2.	In the New Share Wizard, on the Select profile for this share page, in the File share profile box, select NFS Share-Quick and then select Next.
![nfs_share_-2.png](/configure-iscsi-storage/nfs_share_-2.png){.align-left}
3.	On the Select the server and path for this share page, select the Target Server, select by volume, select K, and then select Next.
![nfs_share_-_3.png](/configure-iscsi-storage/nfs_share_-_3.png){.align-left}
4.	On the Specify share name page, in the Share name text box, enter LinuxData and then select Next.
![nfs_share_-_4.png](/configure-iscsi-storage/nfs_share_-_4.png){.align-left}
5.	On the Specify authentication methods page, select Kerberos v5 authentication and then select Next.
![nfs_share_-_5.png](/configure-iscsi-storage/nfs_share_-_5.png){.align-left}
6.	On the Specify the share permissions page, select Add.
![nfs_share_-_6.png](/configure-iscsi-storage/nfs_share_-_6.png){.align-left}
7.	In the Add Permissions window select All Machines.
![nfs_share_-_7.png](/configure-iscsi-storage/nfs_share_-_7.png){.align-left}
8.	In the Share Permissions box, select Read/Write and then select Add. (No Screenshot Present)
9.	On the Specify the share permissions page, select Next. 
![nfs_share_-_8.png](/configure-iscsi-storage/nfs_share_-_8.png){.align-left}
10.	On the Specify permissions to control access page, select Customize Permissions, and select Next.
![nfs_share_-_9.png](/configure-iscsi-storage/nfs_share_-_9.png){.align-left}
11.	On the Advanced Security Settings pane, select Add.
![nfs_share_-_10.png](/configure-iscsi-storage/nfs_share_-_10.png){.align-left}
12.	In the Permission Entry pane, select, Select a principal.
![nfs_share_-_11.png](/configure-iscsi-storage/nfs_share_-_11.png){.align-left}
13.	In the Permission Entry pane, enter Domain Users and then select Ok.
![nfs_share_-_12.png](/configure-iscsi-storage/nfs_share_-_12.png){.align-left}
14.	In the Permission Entry pane, under Basic permissions, select Modify, and select Next.
![nfs_share_-_13.png](/configure-iscsi-storage/nfs_share_-_13.png){.align-left}
15.	In the Advanced Security Settings, select Ok.
![nfs_share_-_14.png](/configure-iscsi-storage/nfs_share_-_14.png){.align-left}
16.	In the Specify permissions to control access pane, select Next. (No Screenshot Present)
17.	On the Confirm selections page, select Create.
![nfs_share_-_15.png](/configure-iscsi-storage/nfs_share_-_15.png){.align-left}
18.	On the View results page, select Close.
![nfs_share_-_16.png](/configure-iscsi-storage/nfs_share_-_16.png){.align-left}

**Map iSCSI Share Folder**

1.	Select your File Folder, Right Click This PC, and select Map Network Drive.
![map_iscsi_file_-_1.png](/configure-iscsi-storage/map_iscsi_file_-_1.png){.align-left}
2.	In Map Network Drive, select Drive Letter, Under Folder, type in your server name, and select Browse.  Select Folder you wish to map.
![map_iscsi_file_-_2.png](/configure-iscsi-storage/map_iscsi_file_-_2.png){.align-left}

**Disable the legacy SMB1 protocol**
1.	In Windows PowerShell, Set-SmbServerConfiguration -AuditSmb1Access $true
![disable_smb1_-_1.png](/configure-iscsi-storage/disable_smb1_-_1.png){.align-left}
2.	For the confirmation message, select Yes.
![disable_smb1_-_2.png](/configure-iscsi-storage/disable_smb1_-_2.png){.align-left}
3.	Enter the following, Get-SmbServerConfiguration | FL enable*
![disable_smb1_-_3.png](/configure-iscsi-storage/disable_smb1_-_3.png){.align-left}
4.	Enter the following, Set-SmbServerConfiguration -EnableSMB1Protocol $false
![disable_smb1_-_4.png](/configure-iscsi-storage/disable_smb1_-_4.png){.align-left}
5.	At the confirmation message, select Yes
![nfs_share_-_17.png](/configure-iscsi-storage/nfs_share_-_17.png){.align-left}
6.	Enter the following, Remove-WindowsFeature FS-SMB1
![nfs_share_-_18.png](/configure-iscsi-storage/nfs_share_-_18.png){.align-left}


## Server Security
- Security baselines and hardening
- Windows Firewall Configuration
- Security auditng and monitoring
- BitLocker encryption
## Server Virtualization & Containers
- Hyper-V overview and setup
- Managing virtual machines
- Windows Containers basics
## Automation & Scripting
- PowerShell fundamentals
- Common PowerShell commands for server administration
- Scheduled Tasks and Automation workflows
## Backup & Disaster Recovery
- Window Server Backup Features
- Recovery options and best practices
- Failover Clustering basics
## Monitoring & Performance
- Performance monitoring tools
- Event Viewer and logs
- Resource optimization
## Troubleshooting & Maintenance
- Common issues and resolution steps
- Patch management and updates
- System health checks