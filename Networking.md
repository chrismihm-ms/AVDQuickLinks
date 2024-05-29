# Azure Virtual Desktop Networking
Below is a collection of Azure Virtual Desktop links to help with understanding AVD Networking concepts and guidelines.

- [Understanding Azure Virtual Desktop network connectivity](https://learn.microsoft.com/en-us/azure/virtual-desktop/network-connectivity)
- [Required URLs for Azure Virtual Desktop | Microsoft Learn](https://learn.microsoft.com/en-us/azure/virtual-desktop/safe-url-list?tabs=azure#virtual-machines)
- [Configure RDP Shortpath for Azure Virtual Desktop](https://learn.microsoft.com/en-us/azure/virtual-desktop/configure-rdp-shortpath?tabs=managed-networks) to establish direct connectivity between the remote desktop client and the session host. This provides a number of benefits including:
    - reduces dependency on the Azure Virtual Desktop gateways reducing RTT improving latency-sensitive applications resulting in an improved user experience
    - Increases the bandwidth available for each user session
    - Improves the reliability of each user session
- [Private Endpoints](https://learn.microsoft.com/en-us/azure/private-link/private-endpoint-overview) for profile storage accounts
- [Remote Desktop Protocol (RDP) bandwidth requirements](https://learn.microsoft.com/en-us/azure/virtual-desktop/rdp-bandwidth)
- [Proxy server guidelines for Azure Virtual Desktop](https://learn.microsoft.com/en-us/azure/virtual-desktop/proxy-server-support)
- [Private Link with Azure Virtual Desktop](https://learn.microsoft.com/en-us/azure/virtual-desktop/private-link-overview)