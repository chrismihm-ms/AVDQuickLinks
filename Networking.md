# Azure Virtual Desktop Networking
Below is a collection of Azure Virtual Desktop links to help with understanding AVD Networking concepts and guidelines.

<p>
Traffic flow for Azure Virtual Desktop (AVD). 
- [Azure Virtual Desktop service architecture and resilience](https://learn.microsoft.com/en-us/azure/virtual-desktop/service-architecture-resilience)

#### Feed Discovery:
*Client ↔ Firewall/Router ↔ Internet ↔ Web Service*
 
#### RDP Connection (Reverse Connect Transport):
##### Outbound Traffic:
*Client → Firewall/Router → Internet → RD Gateway*
*Host → Firewall → (possibly a NAT Gateway, which is recommended) → RD Gateway*
##### Inbound Traffic:
*RD Gateway → Internet → Firewall/Router → Client*
*RD Gateway → NAT Gateway → Firewall → Host*
 
The above assumes that the default route is configured to point to a firewall. Technically, the inbound traffic will be routed along the same path as the outbound traffic. However, the key consideration here is that since we are using **Reverse Connect**, the traffic is always initiated from both the client and the host. This means that it will be trusted by any **stateful firewall** (such as Azure Firewall), so inbound rules won't apply in this case.
 
For **RDP Shortpath** over public networks, the traffic (using ICE/STUN or TURN) will also be initiated from both the client and the host. As such, the same concept of **trusted traffic** applies here as well.
</p>

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
- [Azure network round-trip latency statistics | Microsoft Learn](https://learn.microsoft.com/en-us/azure/networking/azure-network-latency?tabs=Americas%2CWestUS)

\
[*Back to Azure Virtual Desktop (AVD) Quick Reference Links Guide Contents*](https://github.com/chrismihm-ms/AVDQuickLinks/blob/main/README.md#azure-virtual-desktop-avd-quick-reference-links)