# Initial Deployments
Descritpion .....

- [Customer Qualification Questions](https://view.officeapps.live.com/op/view.aspx?src=https%3A%2F%2Fazgearupstorageprod.azureedge.net%2Fassets%2FAzure%2520Virtual%2520Desktop%2520-%2520Customer%2520Qualification%2520Questions.xlsx%3Fsv%3D2019-07-07%26sr%3Db%26sig%3Dye9aFbOr69RgAXTTIX0%252Bg4LOefCgT%252Fz%252BFIl6fBo%252Bu20%253D%26se%3D2023-02-16T19%253A08%253A49Z%26sp%3Dr&wdOrigin=BROWSELINK)
- Azure Landing Zone: [CAF Azure Landing Zone Accelerator](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/implementation-options#azure-landing-zone-accelerator-approach)
- Native AVD Accelerator and Reference Architecture
    - [AVD Accelerator deployment automation to simplify the setup of AVD (Azure Virtual Desktop) based on best practices for Azure Virtual Desktop for the enterprise - Azure Architecture Center | Microsoft Learn](https://github.com/Azure/avdaccelerator)
- Design considerations
    - [Microsoft Azure Well-Architected Framework](https://learn.microsoft.com/en-us/azure/architecture/framework) set of guiding tenets that can be used to improve the quality of a workload
    - [Identity and Access Management](https://learn.microsoft.com/en-us/azure/virtual-desktop/authentication)
    - [Azure Virtual Desktop limitations](https://learn.microsoft.com/en-us/azure/architecture/example-scenario/wvd/windows-virtual-desktop?context=%2Fazure%2Fvirtual-desktop%2Fcontext%2Fcontext#azure-virtual-desktop-limitations)
    - [VM Sizing](https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/virtual-machine-recs) Whether you're running your session host virtual machines (VM) on Remote Desktop Services or Azure Virtual Desktop, different types of workloads require different VM configurations. The examples in this article are generic guidelines and you should only use them for initial performance estimates. For the best possible experience, you will need to scale your deployment depending on your users' needs.
    - [Networking](Networking.md)
    - [User Profiles and Profile Management](Profile%20Management.md)
    - [Image Management](Image%20Management.md)

<p>For organizations looking to leverage Citrix in conjunction with AVD, below are some Citrix Accelerators and Reference Architecture</p>

- [Enterprise-scale support for Citrix on Azure](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/wvd/landing-zone-citrix/citrix-enterprise-scale-landing-zone)
- [Citrix Accelerator](https://github.com/Azure/avdaccelerator/tree/main/workload/docs/citrixlzaccelerator)
- [Citrix Virtual Apps and Desktops Service on Azure](https://docs.citrix.com/en-us/tech-zone/design/reference-architectures/virtual-apps-and-desktops-azure.html)
- [PoC Guide: Citrix Virtual Apps and Desktops with Azure Virtual Desktop Hybrid](https://docs.citrix.com/en-us/tech-zone/learn/poc-guides/cvads-windows-virtual-desktops.html)
- [Reference Architecture: Citrix DaaS - Azure | Citrix Tech Zone](https://docs.citrix.com/en-us/tech-zone/design/reference-architectures/virtual-apps-and-desktops-azure.html)
- [Optimization Recommendations for Citrix Virtual Apps and Desktops](https://docs.citrix.com/en-us/tech-zone/toc/by-product/citrix-virtual-apps-and-desktops/optimizations.html?utm_source=linkedin&utm_campaign=citrix%2520organic&utm_medium=social%2520media%2520organic)