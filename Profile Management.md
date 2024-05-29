# Azure Virtual Desktop Profile Management
The Azure Virtual Desktop service recommends FSLogix profile containers as a user profile solution. FSLogix is designed to roam profiles in remote computing environments, such as Azure Virtual Desktop. It stores a complete user profile in a single container. At sign in, this container is dynamically attached to the computing environment using natively supported Virtual Hard Disk (VHD) and Hyper-V Virtual Hard disk (VHDX). The user profile is immediately available and appears in the system exactly like a native user profile. This article describes how FSLogix profile containers used with Azure Files function in Azure Virtual Desktop. 

## *FXLogix*
- [FSLogix profile containers and Azure files](https://learn.microsoft.com/en-us/azure/virtual-desktop/fslogix-containers-azure-files)
- [Storage options for FSLogix profile containers in Azure Virtual Desktop](https://learn.microsoft.com/en-us/azure/virtual-desktop/store-fslogix-profile)
- [Set up FSLogix Profile Container with Azure Files and AD DS or Azure AD DS](https://learn.microsoft.com/en-us/azure/virtual-desktop/fslogix-profile-container-configure-azure-files-active-directory?tabs=adds)
- [Configure FSLogix Cloud Cache Tutorial](https://learn.microsoft.com/en-us/fslogix/configure-cloud-cache-tutorial)
- [Learn here how to configure Azure Files with Active Directory (AD)](https://www.christiaanbrinkhoff.com/2020/03/01/learn-here-how-to-configure-azure-files-with-active-directory-ad-authentication-for-fslogix-profile-container-and-msix-app-attach/)


## *Storage Consideration* 
- [Storage options for FSLogix profile containers in Azure Virtual Desktop](https://learn.microsoft.com/en-us/azure/virtual-desktop/store-fslogix-profile)

###_Azure Files_
- ***Use Case:*** General Purpose
- ***Regional availability:*** All regions
- ***Redundancy:*** Locally redundant, zone-redundant, geo-redundant, geo-zone-redundant
- ***Tiers and performance:*** Standard (Transaction optimized), Premium Up to max 100K IOPS per share with 10 GBps per share at about 3-ms latency
- ***Capacity:*** 100 TiB per share, Up to 5 PiB per general purpose account
- ***Required infrastructure:*** Minimum share size 1 GiB
- ***Protocols:*** SMB 3.0/2.1, NFSv4.1 (preview), REST

###_Azure Netapp Files_
- ***Use Case:*** General purpose to enterprise scale
Regional availability: [Select regions](https://azure.microsoft.com/explore/global-infrastructure/products-by-region/?products=netapp&regions=all&rar=true)
- ***Redundancy:*** Locally redundant/geo-redundant with cross-region replication
- ***Tiers and performance:*** Standard, Premium, Ultra Up to max 460K IOPS per volume with 4.5 GBps per volume at about 1 ms latency. For IOPS and performance details, see [Azure NetApp Files performance considerations](https://learn.microsoft.com/en-us/azure/azure-netapp-files/azure-netapp-files-performance-considerations) and the [FAQ](https://learn.microsoft.com/en-us/azure/azure-netapp-files/faq-performance#how-do-i-convert-throughput-based-service-levels-of-azure-netapp-files-to-iops).
- ***Capacity:*** 100 TiB per volume, up to 12.5 PiB per NetApp account
- ***Required infrastructure:*** Minimum capacity pool 2 TiB, min volume size 100 GiB
- ***Protocols:*** NFSv3, NFSv4.1, SMB 3.x/2.x, dual-protocol
