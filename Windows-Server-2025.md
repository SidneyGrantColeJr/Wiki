---
title: Windows Server 2025 Administration
description: 
published: true
date: 2025-05-27T16:04:09.669Z
tags: windows server
editor: markdown
dateCreated: 2025-05-16T10:33:58.170Z
---


<span id="top"></span>
## Contents
- [Overview](#overview)
- [Installation and Configuration](#installation-and-configuration)
- [Active Directory AD DS](#active-directory-ad-ds)
- [Networking Services](#networking-services)
- [File and Storage Services](#file-and-storage-services)
- [Configure Basic Storage](#configure-basic-storage)
- [Configure Dynamic Storage](#configure-dynamic-storage)
- [Configure a Storage Pool](#configure-a-storage-pool)
- [Configure a Storage Space](#configure-a-storage-space)
- [Configure iSCSI Storage with MPIO](#configure-iscsi-storage-with-mpio)
- [Server Security](#server-security)
- [Configure Active Directory Certificate Services](#configure-active-directory-certificate-services)
- [Configure Active Directory Federation Services](#configure-active-directory-federation-services)
- [Server Virtualization and Containers](#server-virtualization-and-containers)
- [Automation and Scripting](#automation-and-scripting)
- [Backup and Disaster Recovery](#backup-and-disaster-recovery)
- [Monitoring and Performance](#monitoring-and-performance)
- [Troubleshooting and Maintenance](#troubleshooting-and-maintenance)


## Overview
<a href="#top">Back to top</a>
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

<a href="#top">Back to top</a>

## Installation and Configuration
- System requirements and hardware planning
- Installation options (GUI, Core, Nano)
- Post-installation configuration
- Licensing and activation

<a href="#top">Back to top</a>
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

<a href="#top">Back to top</a>

- Managing users, groups, and organizational units (OUs)
<a href="#top">Back to top</a>
- Group Policy Basics and Management
<a href="#top">Back to top</a>
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

<a href="#top">Back to top</a>











- DNS server setup and management
<a href="#top">Back to top</a>
- Network policy and access services (NPS)
<a href="#top">Back to top</a>
- Remote Access (VPN, Direct Access)
<a href="#top">Back to top</a>
## File and Storage Services
- File Server roles and features
<a href="#top">Back to top</a>
- NTFS and Permissions
<a href="#top">Back to top</a>
- Distributed Files System (DFS)
<a href="#top">Back to top</a>
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

<a href="#top">Back to top</a>
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

<a href="#top">Back to top</a>
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

<a href="#top">Back to top</a>
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

<a href="#top">Back to top</a>
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

<a href="#top">Back to top</a>
## Server Security
- Security baselines and hardening
<a href="#top">Back to top</a>
- Windows Firewall Configuration
<a href="#top">Back to top</a>
- Security auditng and monitoring
<a href="#top">Back to top</a>
- BitLocker encryption
<a href="#top">Back to top</a>
### Configure Active Directory Certificate Services
> **Active Directory Certificate Services (AD CS)** is a Windows Server role that provides public key infrastructure (PKI) for issuing and managing digital certificates.  Certificates are used for secure communication, authentication, and encryption across networks.  Some Key Features of AD CS are the following:
> - **Certification Authorities (CAs)** - Issue and manage certificates for users, computers, and services.
> - **WebEnrollment** - Allows users to request certificates via a web browser.
> - **Onlline Responder** - Provides real-time certificate revocation status.
> - **Network Device Enrollment Service (NDES)** - Enables network devices without domain accounts to obtain certificates.
> - **TPM Key Attestation** - Ensures private keys are protected by trusted hardware.
> - **Certificate Enrollment Services** - Helps users and computers enroll for certificates securely.
{.is-info}

**Deploy an offline root CA**
1.	In Server Manager, from the manage drop-down, select Add roles and features.
![step_1.png](/active-directory-certificate-services/step_1.png)

2.	In the Before you begin pane, select Next.
![step_2.png](/active-directory-certificate-services/step_2.png)

3.	In the Select installation type pane, select Next.
![step_3.png](/active-directory-certificate-services/step_3.png)

4.	In the Select destination server pane, select Next.
![step_4.png](/active-directory-certificate-services/step_4.png)

5.	In the Select server roles pane, select Active Directory Certificate Services.
![step_5.png](/active-directory-certificate-services/step_5.png)

6.	In the Add Roles and Features Wizard pane, select Add Features , and then select Next.
![step_6.png](/active-directory-certificate-services/step_6.png)

7.	In the Select features pane, select Next.
![step_7.png](/active-directory-certificate-services/step_7.png)

8.	In the Active Directory Certificate Services pane, select Next.
![step_8.png](/active-directory-certificate-services/step_8.png)

9.	In the Select Role services pane, ensure Certification Authority is selected, and then select Next.
![step_9a.png](/active-directory-certificate-services/step_9a.png)

10.	In the Confirm installation selections pan, select Install.
![step_10.png](/active-directory-certificate-services/step_10.png)

11.	After the installation completes, select Configure Active Directory Certificate Services in the destination link.
![step_11.png](/active-directory-certificate-services/step_11.png)

12.	In the AD CS Configuration Wizard, in the Credentials pane, select Next.
![step_12.png](/active-directory-certificate-services/step_12.png)

13.	In the Role Services pane, select Certification Authority, and then select Next.
![step_13.png](/active-directory-certificate-services/step_13.png)

14.	In the Setup Type pane, ensure Standalone CA is selected, and then select Next.
![step_14.png](/active-directory-certificate-services/step_14.png)

15.	In the CA Type pane, ensure that Root CA is selected, and then select Next.
![step_15.png](/active-directory-certificate-services/step_15.png)

16.	In the Private Key pane, ensure that Create a new private key is selected, and then select Next.
![step_16.png](/active-directory-certificate-services/step_16.png)

17.	In the Cryptography for CA pane, keep the default selections for Select a cryptographic provider and Select the has algorithm for signing certificates issued by this CA, but set the Key length to 4096, and then select Next.
![step_17.png](/active-directory-certificate-services/step_17.png)

18.	In the CA Name pane, in the Common name for this CA text box, enter a name for the Root CA, ex. COLERootCA, and select Next.
![step_18.png](/active-directory-certificate-services/step_18.png)

19.	In the Validity Period pane, select Next.
![step_19.png](/active-directory-certificate-services/step_19.png)

20.	In the CA Database pane, select Next.
![step_20.png](/active-directory-certificate-services/step_20.png)

21.	In the Confirmation pane, select Configure.
![step_21.png](/active-directory-certificate-services/step_21.png)

22.	In the results pane, select Close.
![step_22.png](/active-directory-certificate-services/step_22.png)

23.	In the Installation progress pane, select Close.
![step_23.png](/active-directory-certificate-services/step_23.png)

24.	In Server Manager, select Tools, and then select Certification Authority.
![step_24.png](/active-directory-certificate-services/step_24.png)

25.	In the certsrv –(Certification Authortiy (Local), in the center pane, right click your Certification Authority, i.e (COLERootCA, and then select Properties.
![step_25.png](/active-directory-certificate-services/step_25.png)

26.	In the Properties dialog box, select the Extensions tab.
![step_26.png](/active-directory-certificate-services/step_26.png)

27.	In the Select extension drop-down list, select CRL Distribution Point (CDP), and then select Add.
![step_27.png](/active-directory-certificate-services/step_27.png)

28.	In the Location text box, enter appropriate server name, i.e. http://IntermediateCA.cole.local/CertData/ 
![step_28.png](/active-directory-certificate-services/step_28.png)

29.	In the Variable drop-down list, select CAName, and then select Insert.
![step_29.png](/active-directory-certificate-services/step_29.png)

30.	In the Variable drop-down list, select CRLNameSuffix, and then select Insert
![step_30.png](/active-directory-certificate-services/step_30.png)

31.	In the Variable drop-down list, select DeltaCRLAllowed, and then select Insert.
![step_31.png](/active-directory-certificate-services/step_31.png)

32.	In the Location text box, position the cursor at the end of the URL, and enter .crl, and then select Ok.
![step_32.png](/active-directory-certificate-services/step_32.png)

33.	Select the following options, and then select Apply:
Include in the CDP extension of issued certificates
Include in the CRLs. Clients use this to find Delta CRL locations.
![step_33.png](/active-directory-certificate-services/step_33.png)

34.	In the Certification Authority window, select No.
![step_34.png](/active-directory-certificate-services/step_34.png)

35.	In the Select extension drop-down list, select Authority Information Access (AIA), and then select Add.
![step_35.png](/active-directory-certificate-services/step_35.png)

36.	In the Location text box, enter enter appropriate server name, i.e. https://IntermediateCA/CertData/
![step_36.png](/active-directory-certificate-services/step_36.png)

37.	In the Variable drop-down list, select ServerDNSName, and then select Insert.
![step_37.png](/active-directory-certificate-services/step_37.png)

38.	In the Location text box, enter an underscore, and in the Variable drop-down list, select CaName, and then select Insert. Position the cursor at the end of the URL.
![step_38.png](/active-directory-certificate-services/step_38.png)

39.	In the Variable drop-down list, select CertificateName, and then select Insert.
![step_39.png](/active-directory-certificate-services/step_39.png)

40.	In the Location text box, position the cursor at the end of the URL, enter .crt, and then select Ok.
![step_40.png](/active-directory-certificate-services/step_40.png)

41.	Select the Include in the AIA extension of issued certificates check box, and then select Ok.
![step_41.png](/active-directory-certificate-services/step_41.png)

42.	Select Yes to restart the Certification Authority service.
![step_42.png](/active-directory-certificate-services/step_42.png)

43.	In the Certification Authority console, expand the RootCA, right-click Revoked Certificates, point to All Tasks, and then select Publish.
![step_43.png](/active-directory-certificate-services/step_43.png)

44.	In the Publish CRL window, select Ok.
![step_44.png](/active-directory-certificate-services/step_44.png)

45.	Right-click the RootCA and then select Properties.
![step_45.png](/active-directory-certificate-services/step_45.png)

46.	In the RootCA Properties dialog box, select View Certificates.
![step_46.png](/active-directory-certificate-services/step_46.png)

47.	In the Certificate dialog box, select Details tab, and then select Copy to File.
![step_47.png](/active-directory-certificate-services/step_47.png)

48.	In the Certificate Export Wizard, in the Welcome pane, select Next.
![step_48.png](/active-directory-certificate-services/step_48.png)

49.	In the Export File Format pane, select DER encoded binary X.509 (.CER), and then select Next.
![step_49.png](/active-directory-certificate-services/step_49.png)

50.	In the File to Export pane, select Browse, in the File name text box, enter, ie. \\IntermediateCA\C$\RootCA.cer, and then select Enter and then Next.
![step_50.png](/active-directory-certificate-services/step_50.png)

51.	Select Finish, and then select Ok three times.
![step_51.png](/active-directory-certificate-services/step_51.png)

52.	Open a File Explorer window, browse to C:\Windows\System32\CertSrv\CerttEnroll.
![step_52.png](/active-directory-certificate-services/step_52.png)

53.	In the CertEnroll folder, select both files and copy.
![step_53.png](/active-directory-certificate-services/step_53.png)

54.	In the File Explore address bar, enter \\IntermediateCA\C$, and then select Enter. Navigate to the CertData Folder.
![step_53a.png](/active-directory-certificate-services/step_53a.png)

55.	Right-click and then paste the files copied earlier.
![step_54.png](/active-directory-certificate-services/step_54.png)

56.	Close the File Explorer.

**Create a Domain Name System record for an offline root CA**

1.	On your Domain Controller, in Server Manager, select Tools, and then select DNS.
![step_55.png](/active-directory-certificate-services/step_55.png)

2.	Right-click the Domain under Forward Lookup Zones, and then select New Host (A or AAAA).
![step_56.png](/active-directory-certificate-services/step_56.png)

3.	In the new Host window, in the Name text box, enter CA-SRV1
![step_57.png](/active-directory-certificate-services/step_57.png)

4.	In the IP Address, enter the IP Address, select Add Host, and then select Ok, then Done.
5.	Close DNS Manager.
![step_58.png](/active-directory-certificate-services/step_58.png)

**Install and Configure AD CS on a separate Server – The Intermediate CA Authority**

1.	In Server Manager, from the manage drop-down, select Add roles and features.
![step_59.png](/active-directory-certificate-services/step_59.png)

2.	In the Before you begin pane, select Next.
![step_60.png](/active-directory-certificate-services/step_60.png)

3.	In the Select installation type pane, select Next.
![step_61.png](/active-directory-certificate-services/step_61.png)

4.	In the Select destination server pane, select Next.
![step_62.png](/active-directory-certificate-services/step_62.png)

5.	In the Select server roles pane, select Active Directory Certificate Services.
![step_63.png](/active-directory-certificate-services/step_63.png)

6.	In the Add Roles and Features Wizard pane, select Add Features , and then select Next.
![step_64.png](/active-directory-certificate-services/step_64.png)

7.	In the Select features pane, select Next.
![step_65.png](/active-directory-certificate-services/step_65.png)

8.	In the Active Directory Certificate Services pane, select Next.
![step_66.png](/active-directory-certificate-services/step_66.png)

9.	In the Select Role services pane, ensure both Certification Authority and Certification Autority Web Enrollment is selected, and then select Next.
![step_67.png](/active-directory-certificate-services/step_67.png)

10.	In the Confirm installation selections pan, select Install.
![step_68.png](/active-directory-certificate-services/step_68.png)

11.	After the installation completes, select Configure Active Directory Certificate Services in the destination link.
![step_69.png](/active-directory-certificate-services/step_69.png)

12.	In the AD CS Configuration Wizard, in the Credentials pane, select Next.
![step_70.png](/active-directory-certificate-services/step_70.png)

13.	In the Role Services pane, select Certification Authority and Certification Authority Web Enrollment, and then select Next.
![step_71.png](/active-directory-certificate-services/step_71.png)

14.	In the Setup Type pane, select Enterprise CA, and then select Next.
![step_72.png](/active-directory-certificate-services/step_72.png)

15.	In the CA Type pane, select Subordinate CA, and then select Next.
![step_73.png](/active-directory-certificate-services/step_73.png)

16.	In the Private Key pane, ensure that Create a new private key is selected, and then select Next.
![step_74.png](/active-directory-certificate-services/step_74.png)

17.	In the Cryptography for CA pane, keep the default selections, and then select Next.
![step_75.png](/active-directory-certificate-services/step_75.png)

18.	In the CA Name pane, in the Common Name for this CA text box, enter Cole-IssuingCA, and then select Next.
![step_76.png](/active-directory-certificate-services/step_76.png)

19.	In the Certificate Request pane, ensure that Save a certificate request to file on the target machine is selected, and then select Next.
![step_77.png](/active-directory-certificate-services/step_77.png)

20.	In the CA Database pane, select next.
![step_78.png](/active-directory-certificate-services/step_78.png)

21.	In the Confirmation pane, select Configure.
![step_79.png](/active-directory-certificate-services/step_79.png)

22.	In the Results pane, ignore the warning messages, and then Close.
![step_80.png](/active-directory-certificate-services/step_80.png)

23.	In the Installation progress pane, select Close.
![step_81.png](/active-directory-certificate-services/step_81.png)

**Install a subordinate CA Certificate**

1.	On the Intermediate CA, Open File Explorer, browse to Local Disk C:
![step_82.png](/active-directory-certificate-services/step_82.png)

2.	Right-click RootCA.cer, and then select Install Certificate.
![step_83.png](/active-directory-certificate-services/step_83.png)

3.	In the Certificate Import Wizard, select Local Machine, and then select Next.
![step_84.png](/active-directory-certificate-services/step_84.png)

4.	In the Certificate Store pane, select Place All certificates in the following store, and then select Browse.
![step_85.png](/active-directory-certificate-services/step_85.png)

5.	Select Trusted Root Certification Authorities, select Ok, select Next, and then select Finish.
![step_86.png](/active-directory-certificate-services/step_86.png)

6.	When the Certificate Import Wizard window appears, select Ok.
![step_87.png](/active-directory-certificate-services/step_87.png)

7.	In the File Explorer window, select the .crl and .crt files, right-click and copy both files.
![step_88.png](/active-directory-certificate-services/step_88.png)

8.	Open the inetpub folder, and then open the wwwroot folder.
![step_89.png](/active-directory-certificate-services/step_89.png)

9.	Create a new folder, and then name it CertData.
![step_90.png](/active-directory-certificate-services/step_90.png)

10.	Paste the two copied files in the CertData folder.
![step_91.png](/active-directory-certificate-services/step_91.png)

11.	Return to Local Disk C:
![step_92.png](/active-directory-certificate-services/step_92.png)

12.	Right-click .req file and copy.
![step_93.png](/active-directory-certificate-services/step_93.png)

13.	In the File Explorer Address bar, enter \\(Your Offline Root Server Name, and then Enter.
![step_94.png](/active-directory-certificate-services/step_94.png)

14.	In the File Explorer window, right-click and paste the files.
![step_95.png](/active-directory-certificate-services/step_95.png)

15.	Switch to the CA Server.

16.	In the Certificate Authority console, right-click the RootCA, point to All Tasks, and select Submit new request.
![step_96.png](/active-directory-certificate-services/step_96.png)

17.	In the Open Request File window, navigate to Local Disk C:, select the .req file and then select Open.
![step_97.png](/active-directory-certificate-services/step_97.png)

18.	In the Certification Authority, select Pending Requests container, right-click and then select Refresh.
![step_98.png](/active-directory-certificate-services/step_98.png)

19.	In the details pane, right-click, point to All Tasks, and then select Issue.
![step_99.png](/active-directory-certificate-services/step_99.png)

20.	In the Certification Authority pane, select the Details tab, and then select Copy to File.
![step_100.png](/active-directory-certificate-services/step_100.png)

21.	In the Certificate Export wizard, in the Welcome pane, select Next.
![step_101.png](/active-directory-certificate-services/step_101.png)

22.	In the Export File Format pane, select Cryptographic Message Syntax Standard- PKCS #7 Certificates (.P7B), select Include all certificates in the certification path if possible, and then select Next.
![step_101.png](/active-directory-certificate-services/step_101.png)

23.	In the File to Export pane, in the File name field, enter \\server\C$\SubCA.p7b, and then select Next, select Finish, and then select Ok.
![step_102.png](/active-directory-certificate-services/step_102.png)

24.	Switch back to the Server acting as the Intermediate CA Authority.

25.	In the Server Manager, select Tools, and then select Certification Authority.
![step_103.png](/active-directory-certificate-services/step_103.png)

26.	In the Certification Authority pane, right-click the CA Authority, point to All Tasks, and then select Install CA Certificate.
![step_104.png](/active-directory-certificate-services/step_104.png)

27.	Go to Local Disk C:, select SubCA.p7b file and then select Open.
![step_105.png](/active-directory-certificate-services/step_105.png)

28.	Wait for 20 seconds, and then on the toolbar, select Start this service button to start the CA service.
![step_106.png](/active-directory-certificate-services/step_106.png)

29.	Swith back to the Root CA Server and shut down the server.
![step_107.png](/active-directory-certificate-services/step_107.png)

**Publish a root CA certificate through Group Policy**

1.	In the Server Manager, select Tools, and then select Group Policy Management.
![step_108.png](/active-directory-certificate-services/step_108.png)

2.	In the Group Policy Management pane, expand Forest, expand Domains, expand your Domain, right-click and select Default Domain Policy, and then select Edit.
![step_109.png](/active-directory-certificate-services/step_109.png)

3.	In the Computer Configuration, expand Policies, expand Window Settings, expand Security Settings, expand Public Key Policies, right-click Trusted Root Certification Authorities, select Import, and then select Next.
![step_110.png](/active-directory-certificate-services/step_110.png)

4.	In the File to Import, select Browse.
![step_111.png](/active-directory-certificate-services/step_111.png)

5.	In the file name text box, enter \\IntermediateCA\C$, and then select Enter.
![step_112.png](/active-directory-certificate-services/step_112.png)

6.	Select RootCA.cer, and then select Open.
7.	Select next two times, and then select Finish.
8.	When the Certificate Import Wizard window appears, select Ok.
9.	Close the Group Policy Management Editor and the Group Management Console.

<a href="#top">Back to top</a>
### Configure Active Directory Federation Services

> Active Directory Federation Services (AD FS) is a single sign-on (SSO) solution developed by Microsoft that allows users to access multiple applications across different organizations using a signle set of credentials.  It enables federated identity management, meaning users can authenticate once and gain access to various systems without needing to log in separately.
> 
> Key Features of AD FS:
> - Claimes-Based Authentication - Uses security tokens with claims about a user's identity instead of a traditional username/password authentication.
> - Federated Trust - Establishes trust between different organizations, allowing users to access external applications securely.
> - Integration with Active Directory - Works with Active Directory Domain Services (AD DS) to authenticate users.
> - Support for SAML & OAuth - Enable authentication for web applications using industry-standard protocols.
> - Remote Access - Allows users to securely access AD-integrated applications even when working remotely.
{.is-info}






















<a href="#top">Back to top</a>




## Server Virtualization and Containers
- Hyper-V overview and setup
<a href="#top">Back to top</a>
- Managing virtual machines
<a href="#top">Back to top</a>
- Windows Containers basics
<a href="#top">Back to top</a>
## Automation and Scripting
- PowerShell fundamentals
<a href="#top">Back to top</a>
- Common PowerShell commands for server administration
<a href="#top">Back to top</a>
- Scheduled Tasks and Automation workflows
<a href="#top">Back to top</a>
## Backup and Disaster Recovery
- Window Server Backup Features
<a href="#top">Back to top</a>
- Recovery options and best practices
<a href="#top">Back to top</a>
- Failover Clustering basics
<a href="#top">Back to top</a>
## Monitoring and Performance
- Performance monitoring tools
<a href="#top">Back to top</a>
- Event Viewer and logs
<a href="#top">Back to top</a>
- Resource optimization
<a href="#top">Back to top</a>
## Troubleshooting and Maintenance
- Common issues and resolution steps
<a href="#top">Back to top</a>
- Patch management and updates
<a href="#top">Back to top</a>
- System health checks
<a href="#top">Back to top</a>