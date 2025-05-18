---
title: Windows Server 2025 Administration
description: 
published: true
date: 2025-05-18T14:12:49.165Z
tags: windows server
editor: markdown
dateCreated: 2025-05-16T10:33:58.170Z
---

# Windows Server 2025

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

Install iSCSI Feature

1.  In Server Manager, select Manage menu and then select Add Roles and Features.
![slide_1.png](/configure-iscsi-storage/slide_1.png){.align-left}
2.  In the Add Roles and Features Wizard, on the Before you begin page, select Next.
![slide_2.png](/configure-iscsi-storage/slide_2.png){.align-left}
3. On the Select Installation type page, select Next. (Role-based or feature-based installation.
![slide_3.png](/configure-iscsi-storage/slide_3.png){.align-left}
4. On the Select destination server page, ensure that Select a server from the server pool is selected (Choose your Server), and then select Next.
![slide_4.png](/configure-iscsi-storage/slide_4.png){.align-left}
5. On the Select Server Roles page, expand File and Storage Services, then expand File and iSCSI Services, then select iSCSI Target Server and then select Next. Select Add Features. Select Next.
![select_7.png](/configure-iscsi-storage/select_7.png){.align-left}
6.  On the Select Features page, select Next.
![slide_7.png](/configure-iscsi-storage/slide_7.png){.align-left}
7. On the Confirm installation selections page, select Install.
![slide_8.png](/configure-iscsi-storage/slide_8.png){.align-left}  
8. When the installation completes, select Close.
![slide_9.png](/configure-iscsi-storage/slide_9.png){.align-left}


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