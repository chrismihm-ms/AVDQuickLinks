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
Login to Azure portal and in the search filed at the top of the portal, search for ***"Azure Virtual Desktop"*** and click that to lauch the AVD blade.
![Search for AVD in Azure Portal](/Diagrams/search-avd-blade.png)  

From the AVD Overview page, click on ***"Quickstart"*** blade and then click on ***"Create"*** in the Host Pools tile
![Quickstart Create Host Pool](/Diagrams/QuickStartCreateHostPool.png)  

In *"Create a host pool Basics"* tab, use the dropdown and ****select the subscripion**** you're looking to deploy AVD resources to. Either ****select or "Create new"*** a resourcs Group. Enter in a ***Host Pool name*** and ***select the region*** where the Azure Virtual Desktop object will be created. The metadata for the object will be stored in the geography associated with the region. For Preferred app group type, ***Select between "Desktop" or "RemoteApp"***. For Host pool type, ***Select between "Pooled" or "Personal"***. For Create Session Host Configuration, ***Select No or Yes***. At the bottom click on the ***Next:Session hosts"*** button to move to the next configuration section.
![Create Host Pool Basics Tab](/Diagrams/CreateHostPoolBasics.png)

In the *"Create a host pool Session hosts"* tab, for Add virtual machines, Select ***"Yes"***. Fields will open up for configuring the session hosts. In the Resource Group section, ***select the resrouce group*** that you would like the session hosts to be deployed to. Enter in a ***Name Prefix*** for you session hosts. Virtual machine type is defaulted to ***Azure Virtual machine***. Leave it on that. Select ***Virtual machine location***. For Availability options, select you desired availability option. For POC, we typically set this to ***"No infrastrcuture redundancy required"***. Select the ***Security type*** you want to use. For POC we typically leave the default of ***"Trusted launch virtual machines"***. For Image, select one of the market place images you would like to use. For POC, We typically use the ***"Windows 11 Enterprise multi-session, Version 24H2 + Microsoft 365 Apps"***. Select the ***"Virtual machine size"*** that you would like to use. Enter in the ***"number of VMs"*** (session hosts) you would like to deploy. For OS disk type, Select ***"Standard SSD"*** and for OS disk size leave the ***"Default size (128GiB)"***.

Select the ***"Virtual network"*** and ***"Subnet"*** that you would like the session hosts to use. Select ***"Network security group type"***. For POC, we typically set this to ***"None"***. In the Domain to join section, Select which directory you would like the session hosts to join. For POC, we typically set this to ***"Microsoft Entra ID"***.Enter in a Virtual machine administrator account ***"Username"*** and ***"Password"***. At the bottom click on the ***Next:Workspace"*** button to move to the next configuration section.
![Create Host Pool Session Host Screenshot 1](/Diagrams/CreateHostPoolSessionHost1.png)
![Create Host Pool Session Host Screenshot 2](/Diagrams/CreateHostPoolSessionHost2.png)

In the *"Create a host pool Workspace"* tab, click on ***"Yes"*** to Register desktop app group. In the To this workspace, either select an existing workspace or ***"Create New"***. At the bottom click on the ***Next:Workspace"*** button to move to the next configuration section.
![Create Host Pool Workspace Tab](/Diagrams/CreateHostPoolWorkspace.png)

In the *"Create a host pool Advanced"* tab, leave the defaults. At the bottom click on the ***Next:Tags"*** button to move to the next configuration section.
![Create Host Pool Advanced Tab](/Diagrams/CreateHostPoolAdvanced.png)

In the *"Create a host pool Tags"* tab, enter is desired resource tags. At the bottom click on the ***Next:Review + create"*** button to move to the next configuration section.
![Create Host Pool Tags Tab](/Diagrams/CreateHostPoolTags.png)

In the *"Create a host pool Review + create"* tab, Review the configuration and make sure that it passes Validation. At the bottom, click on the ***Create"*** button to start the creation of the AVD resrouces.
![Create Host Pool Review + create Tab](/Diagrams/CreateHostPoolCreate.png)


**Azure Virtual Desktop**
- [Azure Virtual Desktop documentation](https://learn.microsoft.com/en-us/azure/virtual-desktop/)
- [Microsoft Certified: Azure Virtual Desktop Specialty](https://learn.microsoft.com/en-us/certifications/azure-virtual-desktop-specialty/)
- [Microsoft Learning Path Modules- Azure Virtual Desktop implementation](https://learn.microsoft.com/en-us/training/browse/?terms=azure%20virtual%20desktop&expanded=azure&products=azure-virtual-desktop)
- [Quickstart - Deploy Azure Virtual Desktop with the getting started feature](https://learn.microsoft.com/en-us/azure/virtual-desktop/getting-started-feature?toc=%2Fazure%2Fvirtual-desktop%2Fremote-app-streaming%2Ftoc.json&bc=%2Fazure%2Fvirtual-desktop%2Fbreadcrumb%2Ftoc.json&tabs=new-aadds)

\
[*Back to Azure Virtual Desktop (AVD) Quick Reference Links Guide Contents*](https://github.com/chrismihm-ms/AVDQuickLinks/blob/main/README.md#azure-virtual-desktop-avd-quick-reference-links)