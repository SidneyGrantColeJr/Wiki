---
title: Windows Server 2025 Administration
description: 
published: true
date: 2025-05-27T13:27:40.420Z
tags: windows server
editor: markdown
dateCreated: 2025-05-16T10:33:58.170Z
---



## Contents
- [Overview](#overview)
- [Installation and Configuration](#installation-and-configuration)
- [Active Directory AD DS](#active-directory-ad-ds)
- [Networking Services](#networking-services)
- [File and Storage Services](#file-and-storage-services)
- [Configure Basic Storage](##configure-basic-storage)
- [Configure Dynamic Storage](#configure-dynamic-storage)
- [Configure a Storage Pool](#configure-a-storage-pool)
- [Configure a Storage Space](#configure-a-storage-space)
- [Configure iSCSI Storage with MPIO](#configure-iscsi-storage-with-mpio)
- [Server Security](#server-security)
- [Configure Active Directory Certificate Services](#configure-active-directory-certificate-services)
- [Server Virtualization and Containers](#server-virtualization-and-containers)
- [Automation and Scripting](#automation-and-scripting)
- [Backup and Disaster Recovery](#backup-and-disaster-recovery)
- [Monitoring and Performance](#monitoring-and-performance)
- [Troubleshooting and Maintenance](#troubleshooting-and-maintenance)


## Overview
- What is Windows Server 2025

> Windows Server 2025 is the latest version of Microsoft's server operating system, officially released on November 1, 20-24 and part of the Windows NT Family.  It builds on previous versions with enhanced security, improved performance, and better cloud integration.
{.is-info}

[Windows Server 2025](https://www.microsoft.com/en-us/windows-server/blog/2024/11/04/windows-server-2025-now-generally-available-with-advanced-security-improved-performance-and-cloud-agility/)

- New Features and enhancements

    - **Advanced Security: Includes Active Directory Improvements, SMB over QUIC, and Delegate Managed Service Accounts (dMSA) for better authentication.**
    - **Hybrid Cloud Capabilities: Supports hotpatching via Azure Arc, reducing downtime for security updates.**
    - **Performance Enhancements:  Faster storage options, file compression, and Bluetooth support.**
    - **Updated User Experience:  Features a Windows 11-style desktop, Wi-FI support, and modern Task Manager.**
    - **System Requirements: Requires a 1.4 GHz 64-bit processor, 512 MB RAM (Server Core) or 2 GB RAM (Desktop Experience), and at least 32 GB storage.**
    - **Windows Server 2025 is designed for on-premised, hybrid, and cloud environments**

> ###  Server roles 
> - ***Active Directory Domain Services (AD DS):*** Lets you run a Domain Controller and manage users, groups, devices, and GPOs.
> - ***Active Directory Certificate Services (AD CS):*** Publishes and manages digital certificates.
> - ***Active Directory Federation Services:*** Provides single-sign-on and claims-based auth across trusted partners/cloud apps.
> - ***Active Directory Lightweight Directory Services ()AD LDS):***  A slim LDAP directory for apps that don't need full AD DS.
> - ***Active Directory Rights Management Services (AD RMS):*** Encrypts and applies usage policies to documents and email.
> - ***DHCP Server:***  Resolves names to IPs for internal zones (and can forward/recursively resolve external queries).
> - ***File and Storage Services:***  Classic file shares plus SMB over QUIC, Storage Spaces Direct, deduplication, iSCSI, and more.
> - ***Print and Document Services:*** Central print server with role-based & Universal Print support.
> - ***Remote Access:*** DirectAccess and traditional VPN (RRAS) in one package; can also as as a web application proxy.
> - ***Web Service (IIS):***  Hosts web sites, REST APIs and .NET/ASP.NET apps; includes HTTP/3 and TLS 1.3 by default.
> - ***Windows Server Update Services (WSUS):***  PXE-based OS deployment for bare-metal or VMs.
> - ***Failover Clustering:***  Provides high availability for clustered VMs, files shares, SQL, etc.
> - ***Network Policy and Access Services (NPAS/NPS):***  RADIUS server for Wi-Fi/VPN auth, connection-request policies, and accounting.
> - ***Remote-Desktop Services (RDS):***  Session-based desktops, RemoteApp, and VDI broker.
> - ***Windows Time Service:***  Stratum-0/Stratum-1 compliant time source (now supports PTPv2 hardware timestamping).
> - ***Storage Replica:***  Synchronous or async block-level replication between servers or clusters.
> - ***Windows Admin Center Gateway:***  (Not officially a role in Server Manager, but included) Web-based management console.
> 
> (Roles are installed via Server Manager with the Add Reoles and Features or you can install with PowerShell with the Install-WindowsFeature.

> **Windows Server 2025 Editions**
> Standard
> Datacenter
> Datacenter: Azure Edition 
> Essentials
> Hyper-V Server
> Server Core Installation
> IoT Embedded Variants



## Installation and Configuration
- System requirements and hardware planning
- Installation options (GUI, Core, Nano)
- Post-installation configuration
- Licensing and activation
## Active Directory (AD DS)
- Introduction to AD DS
- Installing and Configuring Domain Controllers

**Creating a Domain Controller**
1. In the Server Manager, from the Manage dropdown, select Add Roles and Features.
![slide_1.png](/slide_1.png){.align-left}

2. In the Add Roles and Features Wizard, in the Before you begin pane, select Next.
![slide_2.png](/slide_2.png){.align-left}

3. In the Add Roles and Features Wizard, in the Select installation type, select Next.
![slide_3.png](/slide_3.png){.align-left}

4. In the Add Roles and Features Wizard, in the Select destination server, select Next.
![slide_4.png](/slide_4.png){.align-left}

5. In the Add Roles and Features Wizard, in the Select server roles, select Active Directory Domain Services.
![slide_5.png](/slide_5.png){.align-left}

6. In the Add Roles and Features Wizard, select Add Features.
![slide_6.png](/slide_6.png){.align-left}

7. In the Add Roles and Features Wizard, in the Select server roles, select Next.
![slide_7.png](/slide_7.png){.align-left}

8. In the Add Roles and Features Wizard, in the Select features pane, select Next.
![slide_8.png](/slide_8.png){.align-left}

9. In the Add Roles and Features Wizard, in the Active Directory Domain Services, select Next.
![slide_9.png](/slide_9.png){.align-left}

10. In the Add Roles and Features Wizard, in the Confirm installation selections, select Install.
![slide_10.png](/slide_10.png){.align-left}

11. In the Add Roles and Features Wizard, in the Installation progress pane, select Close.
![slide_11.png](/slide_11.png){.align-left}

12. In the Server Manager Dashboard, select the yellow flag alert, and select Promote this server to a domain controller.
![slide_12.png](/slide_12.png){.align-left}

13. In the Deployment Configuration pane, select Add a new forest. Type in your root domain name.
![slide_13.png](/slide_13.png){.align-left}

14. In the Domain Controller Options,select Domain Name System (DNS) server, and Global Catalog (GC), and type in your password for the Domain Controller.
![slide_14.png](/slide_14.png){.align-left}

15. In the DNS Options pane, select Next.
![slide_15.png](/slide_15.png){.align-left}

16. In the Additional Options pane, type in your domain name for the NetBIOS domain name.
![slide_16.png](/slide_16.png){.align-left}

17. In the Paths pane, select Next.
![slide_17.png](/slide_17.png){.align-left}

18. In the Review Options pane, select Next.
![slide_18.png](/slide_18.png){.align-left}

19. In the Prerequisites Check pane, select Install.
![slide_19.png](/slide_19.png){.align-left}

20. Restart Server.

**Add a Windows Server to a Domain**
- **Install Active Directory Domain Services**
1. In Server Manager, from the Manage drop-down, select Add Roles and Features.
![step_1.png](/activedirectory/step_1.png)

2. In the Add Roles and Features Wizard, in the Before you begin pane, select Next.
![step_2.png](/activedirectory/step_2.png)

3. In the Select installation type pane, select Role-based or feature-based installation, and then select Next.
![step_3.png](/activedirectory/step_3.png)

4. In the Select destination server, select server and then select Next.
![step_4.png](/activedirectory/step_4.png)

5. In the Select server roles, select Active Directory Domain Services, and then select Next.
![step_7.png](/activedirectory/networking/step_7.png)

6. In the Add Roles and Features Wizard, select Add Features.
![step_8.png](/activedirectory/networking/step_8.png)

7. In the Select server roles pane, select Next.

8. In the Select features pane, select Next.
![step_9.png](/activedirectory/networking/step_9.png)

9. In the Active Directory Domain Services pane, select Next.
![step_10.png](/activedirectory/networking/step_10.png)

10. In the Confirm installation selections, select Install.
![step_11.png](/activedirectory/networking/step_11.png)

11. In the Installation progress pane, select Close.
![step_12.png](/activedirectory/networking/step_12.png)

- **Joint the Windows Server to the Domain**
1. From the Start, type Control Panel and select.
![step_1.png](/activedirectory/networking/step_1.png)

2. From the Control Panel pane, select Network & Internet.
![step_2.png](/activedirectory/networking/step_2.png)

3. From the Network and Internet pane, select Network and Sharing Center.
![step_3.png](/activedirectory/networking/step_3.png)

4. From the Network and Sharing Center pane, select Change Adapter Settings.
![step_4.png](/activedirectory/networking/step_4.png)

5. From the Network Connections pane, right click and select Properties.
![step_6.png](/networking/step_6.png)

6. From the Ethernet Properties dialog box, double click Internet Protocol Version 4 (TCP/IPv4).
![step_7.png](/networking/step_7.png)

7. Select Use the following IP Address and enter a static IP address, Subnect mask and the Default Gateway for your Server. Also, select Use the following DNS Server.  You must use the Primary Domain Controller's DNS IP Address. Select Ok.
![step_8.png](/networking/step_8.png)

8. In the Ethernet Properties dialog box, select Ok and close out of the open windows.
![step_9.png](/networking/step_9.png)

9. Open File Explorer, right click This PC and select Properties.
![step_10.png](/networking/step_10.png)

10. Select Advanced System Settings.

11. In the System Properties pane, select Computer Name.
![step_11.png](/networking/step_11.png)

12. To rename this computer or change its domain or workgroup, click Change.
![step_12.png](/networking/step_12.png). 

14. Enter a Computer name. Select Member of Domain, and enter the Domain name you want to join, and select Ok.D
13. Enter user name and password.
14. Restart the server.

> When you add a second Domain Controller to an Active Diectory environment, replication is automatic.  Active Directory used multi-master replication, meaning changes made on one Domain Controller are synchronized across all Domain Controllers in the Domain.  The Knowledge Consistency Checker dynamically creates replication links between the Domain Controllers, and the system determines the best replication paths based on the site links and the costs.  By default, replication occurs every 15 minutes within a site, but it can be changed to your needs. To force replication, you can use the command, repadmin.
{.is-info}



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
> There are 5 Main Types of Storage Available on Windows Server 2025
> 	- **Basic Disk:**  The Default in Disk Management, Classic MBR/GPT Partitions. No software RAID.
>   - **Dynamic Disk:** You can convert via Disk Management or with PowerShell. Adds OS-level RAID & spanning(striped, mirrored, RAID-5) without Storage Spaces.  There is a 2 TB limit on MBR.
>   - **Storage Spaces Virtual Disk:** Pool of mixed drives.  Shown to the OS as a single virtual disk.
>   - **Virtual Hard Disk(.vhd/.vhdx):** Hyper-V Manager, Disk Management.  A disk in a file for VMs, backups, or native boot.
>   - **iSCSI Virtual Disk (Target Server):** File-back Logical Unit Number (LUN) you export over the network.  Appears to remote hosts as a raw SCSI disk
{.is-info}

### Configure Basic Storage

1. In Server Manager, select Tools and then select Computer Management.
![step_1.png](/storage/step_1.png)

2.  In the Computer Management pane, select Disk Management.
![step_2.png](/storage/step_2.png)

3.  If a new disk is detected, you will be prompted to initialize it. Choose GPT (Recommended for most modern servers); or MBR (For legacy systems.), and select Ok.
![step_3.png](/storage/step_3.png)

4. Right-click the Unallocated space, and select New Simple Volume.
![step_4.png](/storage/step_4.png)

5. In the New Simple Volume Wizard, select Next.
![step_5.png](/storage/step_5.png)

6. In the Specify Volume Size pane, select the size for your Volume, and select Next.
![step_6.png](/storage/step_6.png)

7. In the Assign Drive Letter or Path, select a drive letter, and then select Next.
![step_7.png](/storage/step_7.png)

8. In the Format Partition pane, select your File System Type (exFAT, NTFS (New Technology File System), ReFs (Resilient File System)), select your Allocation unit size, input your Volume LabelTest, select either Perform a quick format or Enable file and folder compression, and then select Ok.
![step_8.png](/storage/step_8.png)

9. In the Completing the New Simple Volume Wizard, review settings, and then select Finish.
![step_9.png](/storage/step_9.png)

10.  The New Simple Volume will no appear in your Disk Management Window.
![step_10.png](/storage/step_10.png)

![comparison_chart.png](/storage/comparison_chart.png)

### Configure Dynamic Storage

![dynamic_disk_explained.png](/storage/dynammicdisk/dynamic_disk_explained.png)
![types_of_dynamic_disks.png](/storage/dynammicdisk/types_of_dynamic_disks.png)

1. In Server Manager, select Tools and then select Computer Management.
![step_1.png](/storage/step_1.png)

2.  In the Computer Management pane, select Disk Management.
![2.png](/storage/dynammicdisk/2.png)

3. Right click the disk label and choose convert to Dynamic Disk.
![1.png](/storage/dynammicdisk/1.png)

4. In the Convert to Dynamic Disk dialog box, select the basic disk you would like to convert, and then select Ok.
![2.png](/storage/dynammicdisk/2.png)

5. In the Disks to Convert dialog box, select Convert.
![3.png](/storage/dynammicdisk/3.png)

6. In the Disk Managemeent pane, read the information displayed, and select Yes.
![4.png](/storage/dynammicdisk/4.png)

7. The Basic Disk will be converted to a Dynamic Disk.
![2.png](/storage/dynammicdisk/2.png)

> Note:  If you revert back to Basic Storage, it will wipe the contents of the disk.

**After you converted your disk to Dynamic Storage, you can create a specific Volume Type, by right clicking and selecting one of four options: New Spanned Volume, New Striped Volume, New Mirrored Volume or New RAID-5 Volume.  Once selected, follow the Wizard.  Note:  You need more than one dynamic disk to implement the above options.**

![dynamic_storage_volume_options.png](/storage/dynamic_storage_volume_options.png)

### Configure a Storage Pool
1. In Server Manager, select File and Storage Services.
![step_1.png](/storage/storagepool/step_1.png)

2. Select Storage Pools.
![step_2.png](/storage/storagepool/step_2.png)

3. In the New Storage Pool Wizard, in the Before you Begin, select Next.
![step_3.png](/storage/storagepool/step_3.png)

4. In the Specify a storage pool name and subsystem pane, enter a name for your Storage Pool and select the group of available disks.
![step_4.png](/storage/storagepool/step_4.png)

5. In the Select physical disks for the storage pool, select your physical disks you want to add to the storage pool.
![step_5.png](/storage/storagepool/step_5.png)

6. In the Confirm selections pane, select Create.
![step_6.png](/storage/storagepool/step_6.png)

7.  The Storage Pool created will appear in your list of Storage Pools.
![step_7.png](/storage/storagepool/step_7.png)

Or you can type Manage Storage Spaces in the Search bar, and select Add a new Storage Pool.

### Configure a Storage Space

1. In Server Manager,in the File and Storage Services, select Storage Pools and then right click the Storage Pool, and select New Virtual Disk.
![step_2.png](/storage/storagepool/step_2.png)

2. In the Select the Storage pool, select the Storage Pool, and select Next.
![step_3.png](/storage/storagepool/step_3.png)

3. In the New Virtual Disk Wizard, in the Before you Begin pane, select Next.
![step_4.png](/storage/storagepool/step_4.png)

4. In the Specify the virtual disk name, enter the Name for the Virtual Disk, and select Next.

5. In the Specify enclosure resiliency pane, select Next.

6. In the Select the storage layout, select Layout (Simple, Mirror, Parity), and then select Next.

7. In the Specify the provisioning type, select Provisioning Type, and then select Next.
![step_5.png](/storage/storagepool/step_5.png)

8. In the Specify the size of the virtual disk, enter the size of your virtual disk, and select Next.
![step_6.png](/storage/storagepool/step_6.png)

9. In the Confirm selections pane, select Create.
![step_7.png](/storage/storagepool/virtualdisk/step_7.png)

10. In the View results pane, select Close.
![step_8.png](/storage/storagepool/virtualdisk/step_8.png)

11. The Virtual Disk is created.
![step_8.png](/storage/storagepool/step_8.png)

> Note:  You must have more than one virtual disk to setup a storage pool.

### Configure iSCSI Storage with MPIO
> iSCSI stands for Internet Small Computer System Interface.  iSCSI Storage is a way to share block-level storage over a standard IP Network. MPIO stands for Multipath I/O.  MPIO is a storage-fault-tolerance and load-balance feature that lets an operating system use two or more physical paths to reach the same block-storage device, in essence it offers redundancy.
{.is-info}

##**Configure iSCSI Storage with MPIO**

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

1.	On the Target Server, select File and Storage Services, and then select Shares.
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
![share_-_14.png](/configure-iscsi-storage/share_-_14.png){.align-left}

14.	When the share creating is complete, select Close.
![share_-_13.png](/configure-iscsi-storage/share_-_13.png){.align-left}


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
- Configure Active Directory Certificate Services
> **Active Directory Certificate Services (AD CS)** is a Windows Server role that provides public key infrastructure (PKI) for issuing and managing digital certificates.  Certificates are used for secure communication, authentication, and encryption across networks.  Some Key Features of AD CS are the following:
> - **Certification Authorities (CAs)** - Issue and manage certificates for users, computers, and services.
> - **WebEnrollment** - Allows users to request certificates via a web browser.
> - **Onlline Responder** - Provides real-time certificate revocation status.
> - **Network Device Enrollment Service (NDES)** - Enables network devices without domain accounts to obtain certificates.
> - **TPM Key Attestation** - Ensures private keys are protected by trusted hardware.
> - **Certificate Enrollment Services** - Helps users and computers enroll for certificates securely.
{.is-info}



## Server Virtualization and Containers
- Hyper-V overview and setup
- Managing virtual machines
- Windows Containers basics
## Automation and Scripting
- PowerShell fundamentals
- Common PowerShell commands for server administration
- Scheduled Tasks and Automation workflows
## Backup and Disaster Recovery
- Window Server Backup Features
- Recovery options and best practices
- Failover Clustering basics
## Monitoring and Performance
- Performance monitoring tools
- Event Viewer and logs
- Resource optimization
## Troubleshooting and Maintenance
- Common issues and resolution steps
- Patch management and updates
- System health checks