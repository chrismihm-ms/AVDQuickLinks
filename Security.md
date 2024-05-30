# Azure Virtual Desktop Security

Security is key for Healthcare customers and this document provides references to security best practices and guides for Azure Virtual Desktop.

HIPAA BAA & HITRUST are key compliance the Healthcare Organizations are mandated to be audited. Azure Virtual Desktop is also one of the Azure services which are in audit scope of HIPAA BAA & HITRUST and you can find the azure compliance offerings at the [link](https://azure.microsoft.com/en-us/resources/microsoft-azure-compliance-offerings)


**Zero Trust Deployment:**

Applying [Zero Trust principles](https://learn.microsoft.com/en-us/security/zero-trust/azure-infrastructure-avd) to your Azure Virtual Desktop deployment is essential for keeping your data safe. Follow these steps to ensure a secure environment**:

 1. Secure your identities with Zero Trust\
 -Verify explicitly & Create a dedicated user account with least privileges

 2. Secure your endpoints with Zero Trust\
 -Confine access to session hosts and their data\
 -Protect data in all three modes: data at rest, data in transit, data in use

 3. Apply Zero Trust principles to Azure Virtual Desktop storage resources\
 -Use least privileged access\
 -Assume breach

 4. Apply Zero Trust principles to hub and spoke Azure Virtual Desktop VNets\
 -Verify explicitly\
 -Assume breach\
 -Specify allowed network traffic flows between hub and spoke VNets with Azure Firewall

 5. Apply Zero Trust principles to Azure Virtual Desktop session hosts\
 -Use double encryption for end-to-end encryption\
 -Enable encryption at host\
 -Secure maintenance for virtual machines\
 -Use Microsoft Defender for Servers for threat detection

 6. Deploy security, governance, and compliance to Azure Virtual Desktop

 7. Deploy secure management and monitoring to Azure Virtual Desktop\
 -Use Azure Virtual Desktop security, governance, management, and monitoring features to improve defenses and collect session host analytics.

![Reference Architecture AVD Diagram](/Diagrams/AVD_Ref_Arc.jpg)

 ** [*Summary provided by Michel Roth Linked in Post*](https://www.linkedin.com/posts/michelroth_azurevirtualdesktop-avd-activity-7048964958729949184-QhvL/)

- [Zero Trust principles to an Azure Virtual Desktop deployment](https://learn.microsoft.com/en-us/security/zero-trust/azure-infrastructure-avd)


**Host Level AVD Security:**

- [Azure Virtual Desktop Security, Governance & Compliance](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/azure-virtual-desktop/eslz-security-governance-and-compliance)
- [Azure Virtual Desktop security best practices - Azure | Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-desktop/security-guide)
- [Use Azure Firewall to protect Azure Virtual Desktop | Microsoft Docs](https://docs.microsoft.com/en-us/azure/firewall/protect-azure-virtual-desktop)
- [How to use Azure Firewall Premium with WVD - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/azure-network-security/how-to-use-azure-firewall-premium-with-wvd/ba-p/2148402)
- [Git Repo to teplates for Create an Azure Firewall Policy for AVD required URLs](https://github.com/Azure/RDS-Templates/tree/master/AzureFirewallPolicyForAVD)
- [Protecting Windows Virtual Desktop environments with Azure Security Center | Azure Blog and Updates | Microsoft Azure](https://azure.microsoft.com/en-us/blog/protecting-windows-virtual-desktop-environments-with-azure-security-center/)
- [Trusted launch for Azure virtual machine](https://docs.microsoft.com/en-us/azure/virtual-machines/trusted-launch)
- [Azure security baseline for Azure Virtual Desktop](https://learn.microsoft.com/en-us/security/benchmark/azure/baselines/azure-virtual-desktop-security-baseline)
- [Supported identities and authentication methods](https://learn.microsoft.com/en-us/azure/virtual-desktop/authentication)
- [Configure Azure Virtual Desktop AD FS single sign-on - Azure | Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-desktop/configure-adfs-sso)


**AVD Client Security & Data Protection:**

- [Set up Azure multifactor authentication for Windows Virtual Desktop - Azure | Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-desktop/set-up-mfa)
- [Enforce Microsoft Entra multifactor authentication for Azure Virtual Desktop using Conditional Access](https://learn.microsoft.com/en-us/azure/virtual-desktop/set-up-mfa?tabs=avd#create-a-conditional-access-policy)
- [Enable conditional access policy for Azure Virtual Desktop - Azure | Microsoft Docs](https://docs.microsoft.com/en-us/azure/virtual-desktop/set-up-mfa#create-a-conditional-access-policy)
- [Azure Virtual Desktop SSO from Windows Remote Desktop Client - Microsoft Q&A](https://docs.microsoft.com/en-us/answers/questions/488168/azure-virtual-desktop-sso-from-windows-remote-desk.html)
- [Screen capture protection in Azure Virtual Desktop](https://learn.microsoft.com/en-us/azure/virtual-desktop/screen-capture-protection)
- [Watermarking in Azure Virtual Desktop](https://learn.microsoft.com/en-us/azure/virtual-desktop/watermarking)