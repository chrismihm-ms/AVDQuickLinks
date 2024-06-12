# Azure Virtual Desktop Cost Optimization
AVD environment costs is typically a major concern for our customers. AVD environments expand quickly and are dynamic. We recommend putting proper cost controls and optimization in place to help mitigate cloud spend risk. 

Typical Azure Virtual Desktop costs areas that are prime for optimization are:
 - Compute
 - OS Disk storage
 - FSLogix storage
 - Networking
 - Monitoring/Log Analytics
 - Backup

Below are some links to help you better understand the total Azure Virtual Desktop Costs and Instance cost comparison to other cloud providers
- [Understanding total Azure Virtual Desktop deployment costs - Azure | Microsoft Learn](https://learn.microsoft.com/en-us/azure/virtual-desktop/understand-estimate-costs)
- [How much the power of #Azure makes #AVD cheaper over time | LinkedIn](https://www.linkedin.com/pulse/how-much-power-azure-makes-avd-cheaper-time-michel-roth/)
- [Unveiling the True Cost: Single-User vs. Multi-User Sessions in Microsoft Azure Virtual Desktop | GO-EUC](https://www.go-euc.com/unveiling-the-true-cost-single-user-vs-multi-user-sessions-in-microsoft-azure-virtual-desktop/)
- [Azure, AWS, GCP Instance Comparison | CloudPrice](https://cloudprice.net/)

# Operational Cost Optimization
Customers can adjust configuration and behavior of resources to reduce operational costs as much as possible without sacrificing end user experience. Here are some recommendations for operational adjustments to improve cost efficiency:
- Select [appropriate VM instance size](https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/virtual-machine-recs) for your session hosts
- Leverage [Azure hybrid benefits](https://learn.microsoft.com/en-us/windows-server/get-started/azure-hybrid-benefit) on qualifying servers
- [Manage VM run time with autoscale scaling plan for Azure Virtual Desktop](https://learn.microsoft.com/en-us/azure/virtual-desktop/autoscale-scaling-plan)
- [Set up Start VM on Connect](https://learn.microsoft.com/en-us/azure/virtual-desktop/start-virtual-machine-connect?tabs=azure-portal)
- Leveraging Microsoft partner solutions like [Nerdio](https://getnerdio.com/academy/6-cost-reduction-strategies-for-azure-virtual-desktop/) and [Citrix](https://www.citrix.com/products/citrix-virtual-apps-and-desktops/resources/azure-virtual-desktop-calculator.html#/) that help organizations by improving user density, reducing network traffic and optimizing compute and storage


# Billing Optimization
Customers can take advantage of Reserved Instances and Savings Plans to reduce billed usage. Before committing to an RI or Savings Plan, be sure the customer has followed the operational guidance above and has a solid understanding of their expected usage.

Reserved Instances
[Reserved Instances](https://learn.microsoft.com/en-us/azure/cost-management-billing/reservations/save-compute-costs-reservations) offer the deepest discount for a specific SKU of VM in a specific region and subscription. Reservations should be used to apply discounted run costs to the minimum steady-state usage of session hosts.

Savings Plans
[Azure Savings Plans](https://learn.microsoft.com/en-us/azure/cost-management-billing/savings-plan/savings-plan-compute-overview) offer a smaller discount for compute resources, but are not limited to a particular SKU, subscription, or region. These are best scoped to the typical AVD usage across all host pools,but excluding any VM SKUs to which Reserved Instances have been applied.

Savings Plan recommendations can be found in both the Azure Advisor and the Savings Plan purchase screen. Azure Advisor will only provide 3-year recommendations for Savings Plans, but the purchase screen will display both 1-year and 3-year options.

Pay As You Go
For long term steady usage of AVD, Reserved Instances and Savings Plans should be applied for the majority of usage. Oversubscribing RIs or SPs can incur unnecessary costs however, so it's best to err on the side of caution and allow transient above average spikes of usage to remain on PAYG plans. For example:

![Cost Optimization Chart](https://learn.microsoft.com/en-us/azure/cost-management-billing/savings-plan/media/choose-commitment-amount/savings-plan-usage-spikes.png "Cost Optimization Chart")

# Ongoing Cost Monitoring and Controls
- Put controls in place to help mitigate cloud spending risks (Azure policy, budgets and spend alerts)
- Check in with your Azure Advisor best practice recommendations for cost savings
- Monitor and Analyze your costs with Microsoft Cost Management

\
[*Back to Azure Virtual Desktop (AVD) Quick Reference Links Guide Contents*](https://github.com/chrismihm-ms/AVDQuickLinks/blob/main/README.md#azure-virtual-desktop-avd-quick-reference-links)