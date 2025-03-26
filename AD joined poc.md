# Azure Virtual Desktop Proof of Concept leveraging Active Directory Authentication for Session Hosts
Below is a basic outlinde of setting up an initial AVD Proof of Concept using AD Authentication to login to AVD session hosts.

***Prereqs***
- Azure Active Directory tenant
- Azure Subscription
- Available Quota in subscription for desired VM instance
- Register Resource Provider - Make sure to register the *Microsoft.DesktopVirtualization* resource provider for your subscription
- Permissions/RBAC - For purposes of PoC, the admin account should have Contributor and User access administrator role scoped to subscription. 
- Hybrid Identity synced from On-Prem Active Directory via Microsoft Entra Connect or Microsoft Entra Domain Services
- Network access to AD domain controller from the virtual network that the AVD sesssion hosts are deployed in for authentication
- Internet access from the VM that gets deployed. For more information, see [Required FQDNs and endpoints for Azure Virtual Desktop](https://learn.microsoft.com/en-us/azure/virtual-desktop/required-fqdn-endpoint)

*See additional Note and screenshots here: [Additional Notes for Prereqs section](https://github.com/chrismihm-ms/AVDQuickLinks/blob/main/poc.md#notes-from-prereqs-section)*

***Overview***
- Create a host pool.
- Create a workspace.
- Create an application group.
- Create session host virtual machines.
- Assign users or groups to the application group for users to get access to desktops and applications.
- Install AVD client and get logged in to test access to AVD VDI

### Create an initial host pool
Login to Azure portal and in the search filed at the top of the portal, search for ***"Azure Virtual Desktop"*** and click that to lauch the AVD blade.
![Search for AVD in Azure Portal](/Diagrams/search-avd-blade.png)  

From the AVD Overview page, click on ***"Quickstart"*** blade and then click on ***"Create"*** in the Host Pools tile
![Quickstart Create Host Pool](/Diagrams/QuickStartCreateHostPool.png)  

In *"Create a host pool Basics"* tab, use the dropdown and ****select the subscripion**** you're looking to deploy AVD resources to. Either ****select or "Create new"*** a resourcs Group. Enter in a ***Host Pool name*** and ***select the region*** where the Azure Virtual Desktop object will be created. The metadata for the object will be stored in the geography associated with the region. For Preferred app group type, ***Select between "Desktop" or "RemoteApp"***. For Host pool type, ***Select between "Pooled" or "Personal"***. For Create Session Host Configuration, ***Select No or Yes***. At the bottom click on the ***Next:Session hosts"*** button to move to the next configuration section.
![Create Host Pool Basics Tab](/Diagrams/CreateHostPoolBasicsAD.png)

In the *"Create a host pool Session hosts"* tab, for Add virtual machines, Select ***"Yes"***. Fields will open up for configuring the session hosts. In the Resource Group section, ***select the resrouce group*** that you would like the session hosts to be deployed to. Enter in a ***Name Prefix*** for you session hosts. Virtual machine type is defaulted to ***Azure Virtual machine***. Leave it on that. Select ***Virtual machine location***. For Availability options, select you desired availability option. For POC, we typically set this to ***"No infrastrcuture redundancy required"***. Select the ***Security type*** you want to use. For POC we typically leave the default of ***"Trusted launch virtual machines"***. For Image, select one of the market place images you would like to use. For POC, We typically use the ***"Windows 11 Enterprise multi-session, Version 24H2 + Microsoft 365 Apps"***. Select the ***"Virtual machine size"*** that you would like to use. Enter in the ***"number of VMs"*** (session hosts) you would like to deploy. For OS disk type, Select ***"Standard SSD"*** and for OS disk size leave the ***"Default size (128GiB)"***.

Select the ***"Virtual network"*** and ***"Subnet"*** that you would like the session hosts to use. Select ***"Network security group type"***. For POC, we typically set this to ***"None"***. In the Domain to join section, Select which directory you would like the session hosts to join. For POC, we typically set this to ***"Microsoft Entra ID"***.Enter in a Virtual machine administrator account ***"Username"*** and ***"Password"***. At the bottom click on the ***Next:Workspace"*** button to move to the next configuration section.
![Create Host Pool Session Host Screenshot 1](/Diagrams/CreateHostPoolSessionHostAD1.png)
![Create Host Pool Session Host Screenshot 2](/Diagrams/CreateHostPoolSessionHostAD2.png)

In the *"Create a host pool Workspace"* tab, click on ***"Yes"*** to Register desktop app group. In the To this workspace, either select an existing workspace or ***"Create New"***. At the bottom click on the ***Next:Workspace"*** button to move to the next configuration section.
![Create Host Pool Workspace Tab](/Diagrams/CreateHostPoolWorkspace.png)

In the *"Create a host pool Advanced"* tab, leave the defaults. At the bottom click on the ***Next:Tags"*** button to move to the next configuration section.
![Create Host Pool Advanced Tab](/Diagrams/CreateHostPoolAdvanced.png)

In the *"Create a host pool Tags"* tab, enter is desired resource tags. At the bottom click on the ***Next:Review + create"*** button to move to the next configuration section.
![Create Host Pool Tags Tab](/Diagrams/CreateHostPoolTags.png)

In the *"Create a host pool Review + create"* tab, Review the configuration and make sure that it passes Validation. At the bottom, click on the ***Create"*** button to start the creation of the AVD resrouces.
![Create Host Pool Review + create Tab](/Diagrams/CreateHostPoolCreate.png)

## Configuring Entra ID Authentication
After the Host pool(s) are created, you will need to ensure that Microsoft Entra single sign-on is configured. To do this go into the Host pool *"RDP properties"*. You are defaulted to the *"Connection Information"* tab.
![RDP Properties Entra Single Sign On](/Diagrams/RDPPropertiesEntraSingleSignOn.png)

Go to *"Advanced"* tab and make sure that the following are in the RDP properties. If they aren't,add them now and *"Save"*.
*targetisaadjoined:i:1*
*enablerdsaadauth:i:1*
![RDP Properties Advanced Tab](/Diagrams/RDPPropertiesAdvanced.png)

We now need to assign users or groups to the provisioned application group. Go to the application group within AVD management and click into the provisioned application group. In the left hand pane, expand the *"Manage"* blade and click into *"Assignments"*. Click on *"Add"* at the top to bring up the *"Select Microsoft Entra users or user groups"*. Select the user(s) or Groups you would like to add and click on the *"Select"* button at the bottom. 
![Adding Users to Application Group](/Diagrams/AddingUserstoApplicationGroup.png)
![Select Microsoft Entra users or user groups](/Diagrams/SelectEntraIDGroup.png)

After the User(s) or Groups are assigned to the Application Group, We need to check that it has the necessary access (or add it) to be able to login in to the session hosts using their Entra ID. Go to the resource group where the session hosts were deployed and click on the *"Access Control (IAM)"* blade. Under *"Role assignments'*, Click on *"Add', Add role assignment* at the top to add the user(s) or groups into the *"Virtual Machine User Login"* role
![Resource Group Role Assignment](/Diagrams/ResourceGroupRoleAssignment.png)

In *"Add role assignment"* management, You are defaulted to the *"Role"* tab. Use the search field to search for  the *"Virtual Machine User Login"* role. Click on it to highlight it and then click on *"Next"* button at the bottom.
AddRoleAssignmentRoll
![Add Role Assignment Role](/Diagrams/AddRoleAssignmentRole.png)

Click on the *"Members"* tab and then click on *"Select members"* to add the user(s)/Groups. Click on *"Review + assign"* button at the bottom twice
![Add Role Assignment](/Diagrams/AddRoleAssignment1.png)
![Add Role Assignment Members](/Diagrams/AddRoleAssignmentMembers.png)

You can confirm by checking the role assignment, you can search for the users or groups and it should show that they are in the *"Virtual Machine User Login"* role assignment.
![Checking Role Assignment Members](/Diagrams/AddRoleAssignmentConfirmation.png)

## Check End User Experience
Login to the AVD Remote Desktop Client with Entra ID and make sure that the workspace with Icon to session host shows up. Click on the Icon to launch and test access to VDI.
![AVD Client Experience](/Diagrams/AVDClient.png)

## Additional Notes for Prereqs section

**Session hosts**
To join session hosts to Microsoft Entra ID or an Active Directory domain, you need the following permissions:
- For Microsoft Entra ID, you need an account that can join computers to your tenant. For more information, see [Manage device identities](https://learn.microsoft.com/en-us/azure/active-directory/devices/manage-device-identities#configure-device-settings). To learn more about joining session hosts to Microsoft Entra ID, see [Microsoft Entra joined session hosts](https://learn.microsoft.com/en-us/azure/virtual-desktop/azure-ad-joined-session-hosts).
- For an Active Directory domain, you need a domain account that can join computers to your domain. For Microsoft Entra Domain Services, you would need to be a member of the [AAD DC Administrators group](https://learn.microsoft.com/en-us/azure/active-directory-domain-services/tutorial-create-instance-advanced#configure-an-administrative-group).

==*The account you use for joining a domain can't have multi-factor authentication (MFA) enabled.*==

**RBAC**
- you can assign the Contributor or Owner RBAC role to create all of these resource types
- must be assigned the following built-in role-based access control (RBAC) roles as a minimum on a resource group or subscription to create the following resource types.

![RBAC Roles](/Diagrams/RBACRoles.png)

Ongoing management of host pools, workspaces, and application groups,
[Built-in Azure RBAC roles Azure Virtual Desktop | Microsoft Learn](https://learn.microsoft.com/en-us/azure/virtual-desktop/rbac)
- To assign users to the application group, you'll also need *Microsoft.Authorization/roleAssignments/write* permissions on the application group.
Built-in RBAC roles that include this permission are [User Access Administrator](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#user-access-administrator) and [Owner](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#owner).

**Must register resource provider**
- Make sure to register the Microsoft.DesktopVirtualization resource provider for your subscription
![Register Resource Provider](/Diagrams/RegisterResourceProvider.png)

### Additional Supporting Links to Microsoft documentation for Azure Virtual Desktop
- [Azure Virtual Desktop documentation](https://learn.microsoft.com/en-us/azure/virtual-desktop/)
- [Microsoft Certified: Azure Virtual Desktop Specialty](https://learn.microsoft.com/en-us/certifications/azure-virtual-desktop-specialty/)
- [Microsoft Learning Path Modules- Azure Virtual Desktop implementation](https://learn.microsoft.com/en-us/training/browse/?terms=azure%20virtual%20desktop&expanded=azure&products=azure-virtual-desktop)
- [Prerequisites for Azure Virtual Desktop](https://learn.microsoft.com/en-us/azure/virtual-desktop/prerequisites?tabs=portal)

- [Quickstart - Deploy Azure Virtual Desktop with the getting started feature](https://learn.microsoft.com/en-us/azure/virtual-desktop/getting-started-feature?toc=%2Fazure%2Fvirtual-desktop%2Fremote-app-streaming%2Ftoc.json&bc=%2Fazure%2Fvirtual-desktop%2Fbreadcrumb%2Ftoc.json&tabs=new-aadds)
- [Supported identities and authentication methods](https://learn.microsoft.com/en-us/azure/virtual-desktop/authentication)

- [Compare Remote Desktop client features across platforms and devices](https://learn.microsoft.com/en-us/previous-versions/remote-desktop-client/compare-remote-desktop-clients?pivots=azure-virtual-desktop&context=%2Fwindows-server%2Fcontext%2Fwindows-server-remote-desktop-services)
- [Install the Remote Desktop client for Windows](https://learn.microsoft.com/en-us/previous-versions/remote-desktop-client/connect-windows-cloud-services?pivots=remote-desktop-msi&tabs=windows-msrdc-msi)
- [the Remote Desktop client for Windows - Windows 64-bit](https://go.microsoft.com/fwlink/?linkid=2139369)

\
[*Back to Azure Virtual Desktop (AVD) Quick Reference Links Guide Contents*](https://github.com/chrismihm-ms/AVDQuickLinks/blob/main/README.md#azure-virtual-desktop-avd-quick-reference-links)