# Azure Virtual Desktop Proof of Concept
Below is a basic outlinde of setting up an initial AVD Proof of Concept.

***Prereqs***
- Azure Active Directory tenant
- Azure Subscription
- Available Quota in subscription for desired VM instance
- Register Resource Provider - Make sure to register the *Microsoft.DesktopVirtualization* resource provider for your subscription
- Permissions/RBAC - For purposes of PoC, the admin account should have Contributor and User access administrator role scoped to subscription. 
- Internet access from the VM that gets deployed. For more information, see [Required FQDNs and endpoints for Azure Virtual Desktop](https://learn.microsoft.com/en-us/azure/virtual-desktop/required-fqdn-endpoint)

***Overview***
- Create a host pool.
- Create a workspace.
- Create an application group.
- Create session host virtual machines.
- Assign users or groups to the application group for users to get access to desktops and applications.

### Create an initial host pool
Login to Azure portal and in the search filed at the top of the portal, search for "Azure Virtual Desktop" and click that to lauch the AVD blade.
![Search for AVD in Azure Portal](/Diagrams/search-avd-blade.png)  

From the AVD Overview page, click on "Create a host pool"
![Create Host Pool Button](/Diagrams/create-host-pool-button.png)  




**Azure Virtual Desktop**
- [Azure Virtual Desktop documentation](https://learn.microsoft.com/en-us/azure/virtual-desktop/)
- [Microsoft Certified: Azure Virtual Desktop Specialty](https://learn.microsoft.com/en-us/certifications/azure-virtual-desktop-specialty/)
- [Microsoft Learning Path Modules- Azure Virtual Desktop implementation](https://learn.microsoft.com/en-us/training/browse/?terms=azure%20virtual%20desktop&expanded=azure&products=azure-virtual-desktop)
- [Quickstart - Deploy Azure Virtual Desktop with the getting started feature](https://learn.microsoft.com/en-us/azure/virtual-desktop/getting-started-feature?toc=%2Fazure%2Fvirtual-desktop%2Fremote-app-streaming%2Ftoc.json&bc=%2Fazure%2Fvirtual-desktop%2Fbreadcrumb%2Ftoc.json&tabs=new-aadds)

\
[*Back to Azure Virtual Desktop (AVD) Quick Reference Links Guide Contents*](https://github.com/chrismihm-ms/AVDQuickLinks/blob/main/README.md#azure-virtual-desktop-avd-quick-reference-links)