---
title: Azure Stack Hub archived known issues 
description: Learn about archived known issues in Azure Stack Hub releases.
author: sethmanheim

ms.topic: article
ms.date: 03/18/2021
ms.author: sethm
ms.reviewer: sranthar
ms.lastreviewed: 09/09/2020
ROBOTS: NOINDEX
---


# Azure Stack Hub archived known issues

This article lists known issues in unsupported Azure Stack Hub releases. The list is updated as new issues are identified.

To access known issues for a different archived version, use the version selector dropdown above the table of contents on the left.

<!---------------------------------------------------------->
<!------------------- SUPPORTED VERSIONS ------------------->
<!---------------------------------------------------------->
::: moniker range=">azs-1910"
## Known issues for supported versions

Known issues for supported versions of Azure Stack Hub can be found under [Overview > Release notes > Known issues](../known-issues.md)
::: moniker-end

<!---------------------------------------------------------->
<!------------------- UNSUPPORTED VERSIONS ----------------->
<!---------------------------------------------------------->
::: moniker range="<=azs-1910"
> [!IMPORTANT]  
> If your Azure Stack Hub instance is behind by more than two updates, it's considered out of compliance. You must [update to at least the minimum supported version to receive support](../azure-stack-servicing-policy.md#keep-your-system-under-support).
::: moniker-end

::: moniker range="azs-1910"
## 1910 archived known issues

This article lists known issues in Azure Stack Hub releases. The list is updated as new issues are identified.

> [!IMPORTANT]  
> If your Azure Stack Hub instance is behind by more than two updates, it's considered out of compliance. You must [update to at least the minimum supported version to receive support](../azure-stack-servicing-policy.md#keep-your-system-under-support).

## Update

For known Azure Stack Hub update issues, see [Troubleshooting Updates in Azure Stack Hub](../azure-stack-troubleshooting.md#troubleshoot-azure-stack-hub-updates).

## Portal

### Administrative subscriptions

- Applicable: This issue applies to all supported releases.
- Cause: The two administrative subscriptions that were introduced with version 1804 should not be used. The subscription types are **Metering** subscription, and **Consumption** subscription.
- Remediation: If you have resources running on these two subscriptions, recreate them in user subscriptions.
- Occurrence: Common

### Duplicate Subscription button in Lock blade

- Applicable: This issue applies to all supported releases.
- Cause: In the administrator portal, the **Lock** blade for user subscriptions has two buttons that say **Subscription**.
- Occurrence: Common

### Subscription permissions

- Applicable: This issue applies to all supported releases.
- Cause: You cannot view permissions to your subscription using the Azure Stack Hub portals.
- Remediation: Use [PowerShell to verify permissions](/powershell/module/azurerm.resources/get-azurermroleassignment).
- Occurrence: Common

### Storage account settings

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the storage account **Configuration** blade shows an option to change **security transfer type**. The feature is currently not supported in Azure Stack Hub.
- Occurrence: Common

### Upload blob with OAuth error

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, when you try to upload a blob using the **OAuth(preview)** option, the task fails with an error message.
- Remediation: Upload the blob using the SAS option.
- Occurrence: Common

### Upload blob option unsupported

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, when you try to upload a blob in the upload blade, there is an option to select **AAD** or **Key Authentication**, however **AAD** is not supported in Azure Stack Hub.
- Occurrence: Common

### Alert for network interface disconnected

- Applicable: This issue applies to 1908 and above.
- Cause: When a cable is disconnected from a network adapter, an alert does not show in the administrator portal. This issue is caused because this fault is disabled by default in Windows Server 2019.
- Occurrence: Common

### Incorrect tooltip when creating VM

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, when you select a managed disk, with disk type Premium SSD, the drop-down list shows **OS Disk**. The tooltip next to that option says **Certain OS Disk sizes may be available for free with Azure Free Account**; however, this is not valid for Azure Stack Hub. In addition, the list includes **Free account eligible** which is also not valid for Azure Stack Hub.
- Occurrence: Common

### Delete a storage container

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, when a user attempts to delete a storage container, the operation fails when the user does not toggle **Override Azure Policy and RBAC Role settings**.
- Remediation: Ensure that the box is checked for **Override Azure Policy and RBAC Role settings**.
- Occurrence: Common

### Refresh button on virtual machines fails

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, when you navigate to **Virtual Machines** and try to refresh using the button at the top, the states fail to update accurately.
- Remediation: The status is automatically updated every 5 minutes regardless of whether the refresh button has been clicked or not. Wait 5 minutes and check the status.
- Occurrence: Common

### Storage account options

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the name of storage accounts is shown as **Storage account - blob, file, table, queue**; however, **file** is not supported in Azure Stack Hub.
- Occurrence: Common

### Storage account configuration

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, when you create a storage account and view its **Configuration**, you cannot save configuration changes, as it results in an AJAX error.
- Occurrence: Common

### Capacity monitoring in SQL resource provider keeps loading

- Applicable: This issue applies to the Azure Stack Hub 1910 update or later, with SQL resource provider version 1.1.33.0 or earlier installed.
- Cause: The current version of the SQL resource provider is not compatible with some of the latest portal changes in the 1910 update.
- Remediation: Follow the resource provider update process to apply the SQL resource provider hotfix 1.1.47.0 after Azure Stack Hub is upgraded to the 1910 update ([SQL RP version 1.1.47.0](https://aka.ms/azurestacksqlrp11470)). For the MySQL resource provider, it is also recommended that you apply the MySQL resource provider hotfix 1.1.47.0 after Azure Stack Hub is upgraded to 1910 update ([MySQL RP version 1.1.47.0](https://aka.ms/azurestackmysqlrp11470)).
- Occurrence: Common

### Access Control (IAM)

- Applicable: This issue applies to all supported releases.
- Cause: The IAM extension is out of date. The Ibiza portal that shipped with Azure Stack Hub introduces a new behavior that causes the RBAC extension to fail if the user is opening the **Access Control (IAM)** blade for a subscription that is not selected in the global subscription selector (**Directory + Subscription** in the user portal). The blade displays **Loading** in a loop, and the user cannot add new roles to the subscription. The **Add** blade also displays **Loading** in a loop.
- Remediation: Ensure that the subscription is checked in the **Directory + Subscription** menu. The menu can be accessed from the top of the portal, near the **Notifications** button, or via the shortcut on the **All resources** blade that displays **Don't see a subscription? Open Directory + Subscription settings**. The subscription must be selected in this menu.

### SQL resource provider

- Applicable: This issue applies to stamps that are running 1908 or earlier.
- Cause: When deploying the SQL resource provider (RP) version 1.1.47.0, the portal shows no assets other than those associated with the SQL RP.
- Remediation: Delete the RP, upgrade the stamp, and re-deploy the SQL RP.

### Activity log blade

- Applicable: This issue applies to stamps that are running 1907 or later. <!-- Note: Applies to 2002 as well -->
- Cause: When accessing the activity log, the portal only shows the first page of entries. **Load more results** will not load addition entries.
- Remediation: Adjust the time range in the filter to review entries that fall after the first page.

## Networking

### Load balancer

#### Error: Failed to save load balancer backend pool

- Applicable: This issue applies to all supported releases.
- Cause: When adding availability set VMs to the backend pool of a load balancer, an error message is displayed on the portal stating **Failed to save load balancer backend pool**. This is a cosmetic issue on the portal; the functionality is still in place and VMs are successfully added to the backend pool internally.
- Occurrence: Common

### Network Security Groups

#### VM deployment fails due to DenyAllOutbound rule

- Applicable: This issue applies to all supported releases. 
- Cause: An explicit **DenyAllOutbound** rule cannot be created in an NSG as this will prevent all internal communication to infrastructure needed for the VM deployment to complete.
- Occurrence: Common

#### Cannot delete an NSG if NICs not attached to running VM

- Applicable: This issue applies to all supported releases.
- Cause: When disassociating an NSG and a NIC that is not attached to a running VM, the update (PUT) operation for that object fails at the network controller layer. The NSG will be updated at the network resource provider layer, but not on the network controller, so the NSG moves to a failed state.
- Remediation: Attach the NICs associated to the NSG that needs to be removed with running VMs, and disassociate the NSG or remove all the NICs that were associated with the NSG.
- Occurrence: Common

### Network interface

#### NIC cannot be added to running VM

- Applicable: This issue applies to all supported releases.
- Cause: A new network interface cannot be added to a VM that is in a **running** state.
- Remediation: Stop the virtual machine before adding or removing a network interface.
- Occurrence: Common

#### VM startup issues after deleting/detaching primary NIC

- Applicable: This issue applies to all supported releases.
- Cause: The primary NIC of a VM cannot be changed. Deleting or detaching the primary NIC results in issues when starting up the VM.
- Occurrence: Common

### Virtual Network Gateway

#### Virtual Network gateway appears as a Next Hop Type routing option

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, when you create a route table, **Virtual Network gateway** appears as one of the next hop type options; however, this is not supported in Azure Stack Hub.
- Occurrence: Common

#### Virtual Network Gateway blade shows option to use Alerts

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **Virtual Network Gateway** blade shows an option to use **Alerts**. This feature is currently not supported in Azure Stack Hub.
- Occurrence: Common

#### Virtual Network Gateway blade shows Active-Active option

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, while creating, and in the resource menu of **Virtual Network Gateway**, you will see an option to enable **Active-Active** configuration. This feature is currently not supported in Azure Stack Hub.
- Occurrence: Common

#### Connections blade shows VPN troubleshooter feature

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **Connections** blade displays a feature called **VPN Troubleshooter**. This feature is currently not supported in Azure Stack Hub.
- Occurrence: Common

#### VPN gateway resource shows VPN Troubleshoot and Metrics feature

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **VPN Troubleshoot** feature and **Metrics** in a VPN gateway resource appears, however this is not supported in Azure Stack Hub.
- Occurrence: Common

#### Documentation links are Azure-specific

- Applicable: This issue applies to all supported releases.
- Cause: The documentation links in the overview page of Virtual Network gateway link to Azure-specific documentation instead of Azure Stack Hub. Use the following links for the Azure Stack Hub documentation:

  - [Gateway SKUs](../../user/azure-stack-vpn-gateway-about-vpn-gateways.md#gateway-skus)
  - [Highly Available Connections](../../user/azure-stack-vpn-gateway-about-vpn-gateways.md#gateway-availability)
  - [Configure BGP on Azure Stack Hub](../../user/azure-stack-vpn-gateway-settings.md#gateway-requirements)
  - [ExpressRoute circuits](../azure-stack-connect-expressroute.md)
  - [Specify custom IPsec/IKE policies](../../user/azure-stack-vpn-gateway-settings.md#ipsecike-parameters)

#### Service endpoints not available

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **Virtual Network** blade shows an option to use **Service Endpoints**. This feature is currently not supported in Azure Stack Hub.
- Occurrence: Common

## Compute

### VM boot diagnostics

- Applicable: This issue applies to all supported releases.
- Cause: When creating a new Windows virtual machine (VM), the following error might be displayed: **Failed to start virtual machine 'vm-name'. Error: Failed to update serial output settings for VM 'vm-name'**. The error occurs if you enable boot diagnostics on a VM, but delete your boot diagnostics storage account.
- Remediation: Recreate the storage account with the same name you used previously.
- Occurrence: Common

### Consumed compute quota

- Applicable: This issue applies to all supported releases.
- Cause: When creating a new virtual machine, you may receive an error such as **This subscription is at capacity for Total Regional vCPUs on this location. This subscription is using all 50 Total Regional vCPUs available.**. This indicates that the quota for total cores available to you has been reached.
- Remediation: Ask your operator for an add-on plan with additional quota. Editing the current plan's quota will not work or reflect increased quota.
- Occurrence: Rare

### Privileged Endpoint

- Applicable: This issue applies to 1910 and earlier releases.
- Cause: Unable to connect to the Privileged Endpoint (ERC VMs) from a computer running a non-English version of Windows.
- Remediation: This is a known issue that has been fixed in releases later than 1910. As a workaround you can run the **New-PSSession** and **Enter-PSSession** PowerShell cmdlets using the **en-US** culture; for examples, set the culture using this script: https://resources.oreilly.com/examples/9780596528492/blob/master/Use-Culture.ps1.
- Occurrence: Rare

### Virtual machine scale set

#### Create failures during patch and update on 4-node Azure Stack Hub environments

- Applicable: This issue applies to all supported releases.
- Cause: Creating VMs in an availability set of 3 fault domains and creating a virtual machine scale set instance fails with a **FabricVmPlacementErrorUnsupportedFaultDomainSize** error during the update process on a 4-node Azure Stack Hub environment.
- Remediation: You can create single VMs in an availability set with 2 fault domains successfully. However, scale set instance creation is still not available during the update process on a 4-node Azure Stack Hub deployment.
::: moniker-end

::: moniker range="azs-1908"
## 1908 archived known issues

This article lists known issues in releases of Azure Stack. The list is updated as new issues are identified.

To access known issues for a different version, use the version selector dropdown above the table of contents on the left.

> [!IMPORTANT]  
> Review this section before applying the update.

> [!IMPORTANT]  
> If your Azure Stack instance is behind by more than two updates, it's considered out of compliance. You must [update to at least the minimum supported version to receive support](../azure-stack-servicing-policy.md#keep-your-system-under-support).

## 1908 update process

- Applicable: This issue applies to all supported releases.
- Cause: When attempting to install the Azure Stack update, the status for the update might fail and change state to **PreparationFailed**. This is caused by the update resource provider (URP) being unable to properly transfer the files from the storage container to an internal infrastructure share for processing.
- Remediation: Starting with version 1901 (1.1901.0.95), you can work around this issue by clicking **Update now** again (not **Resume**). The URP then cleans up the files from the previous attempt, and restarts the download. If the problem persists, we recommend manually uploading the update package by following the [Install updates section](../azure-stack-apply-updates.md#install-updates-and-monitor-progress).
- Occurrence: Common

## Portal

### Administrative subscriptions

- Applicable: This issue applies to all supported releases.
- Cause: The two administrative subscriptions that were introduced with version 1804 should not be used. The subscription types are **Metering** subscription, and **Consumption** subscription.
- Remediation: If you have resources running on these two subscriptions, recreate them in user subscriptions.
- Occurrence: Common

### Subscriptions Properties blade

- Applicable: This issue applies to all supported releases.
- Cause: In the administrator portal, the **Properties** blade for subscriptions does not load correctly
- Remediation: You can view these subscription properties in the **Essentials** pane of the **Subscriptions Overview** blade.
- Occurrence: Common

### Subscriptions Lock blade

- Applicable: This issue applies to all supported releases.
- Cause: In the administrator portal, the **Lock** blade for user subscriptions has two buttons that say **subscription**.
- Occurrence: Common

### Subscription permissions

- Applicable: This issue applies to all supported releases.
- Cause: You cannot view permissions to your subscription using the Azure Stack portals.
- Remediation: Use [PowerShell to verify permissions](/powershell/module/azurerm.resources/get-azurermroleassignment).
- Occurrence: Common

### Storage account settings

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the storage account **Configuration** blade shows an option to change **security transfer type**. The feature is currently not supported in Azure Stack.
- Occurrence: Common

### Upload blob

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, when you try to upload a blob using the **OAuth(preview)** option, the task fails with an error message.
- Remediation: Upload the blob using the SAS option.
- Occurrence: Common

## Networking

### Service endpoints

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **Virtual Network** blade shows an option to use **Service Endpoints**. This feature is currently not supported in Azure Stack.
- Occurrence: Common

### Network interface

- Applicable: This issue applies to all supported releases.
- Cause: A new network interface cannot be added to a VM that is in a **running** state.
- Remediation: Stop the virtual machine before adding/removing a network interface.
- Occurrence: Common

### Virtual Network Gateway

#### Local network gateway deletion

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, deleting the **Local Network Gateway** displays the following error message: **Cannot delete a Local Network Gateway with an active connection**, even though there is no active connection.
- Mitigation: The fix for this issue will be released in 1907. A workaround for this issue is to create a new Local Network Gateway  with the same IP address, address space and configuration details with a different name. The old LNG can be deleted once the environment has been updated to 1907.
- Occurrence: Common

#### Alerts

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **Virtual Network Gateway** blade shows an option to use **Alerts**. This feature is currently not supported in Azure Stack.
- Occurrence: Common

#### Active-Active

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, while creating, and in the resource menu of **Virtual Network Gateway**, you will see an option to enable **Active-Active** configuration. This feature is currently not supported in Azure Stack.
- Occurrence: Common

#### VPN troubleshooter

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **Connections** blade shows a feature called **VPN Troubleshooter**. This feature is currently not supported in Azure Stack.
- Occurrence: Common

#### Documentation

- Applicable: This issue applies to all supported releases.
- Cause: The documentation links in the overview page of Virtual Network gateway link to Azure-specific documentation instead of Azure Stack. Use the following links for the Azure Stack documentation:

  - [Gateway SKUs](../../user/azure-stack-vpn-gateway-about-vpn-gateways.md#gateway-skus)
  - [Highly Available Connections](../../user/azure-stack-vpn-gateway-about-vpn-gateways.md#gateway-availability)
  - [Configure BGP on Azure Stack](../../user/azure-stack-vpn-gateway-settings.md#gateway-requirements)
  - [ExpressRoute circuits](../azure-stack-connect-expressroute.md)
  - [Specify custom IPsec/IKE policies](../../user/azure-stack-vpn-gateway-settings.md#ipsecike-parameters)

## Compute

### VM boot diagnostics

- Applicable: This issue applies to all supported releases.
- Cause: When creating a new Windows virtual machine (VM), the following error may be displayed:
**Failed to start virtual machine 'vm-name'. Error: Failed to update serial output settings for VM 'vm-name'**. The error occurs if you enable boot diagnostics on a VM, but delete your boot diagnostics storage account.
- Remediation: Recreate the storage account with the same name you used previously.
- Occurrence: Common

### Virtual machine scale set

#### Create failures during patch and update on 4-node Azure Stack environments

- Applicable: This issue applies to all supported releases.
- Cause: Creating VMs in an availability set of 3 fault domains and creating a virtual machine scale set instance fails with a **FabricVmPlacementErrorUnsupportedFaultDomainSize** error during the update process on a 4-node Azure Stack environment.
- Remediation: You can create single VMs in an availability set with 2 fault domains successfully. However, scale set instance creation is still not available during the update process on a 4-node Azure Stack.

### Ubuntu SSH access

- Applicable: This issue applies to all supported releases.
- Cause: An Ubuntu 18.04 VM created with SSH authorization enabled does not allow you to use the SSH keys to sign in.
- Remediation: Use VM access for the Linux extension to implement SSH keys after provisioning, or use password-based authentication.
- Occurrence: Common

### Virtual machine scale set reset password does not work

- Applicable: This issue applies to all supported releases.
- Cause: A new reset password blade appears in the scale set UI, but Azure Stack does not support resetting password on a scale set yet.
- Remediation: None.
- Occurrence: Common

### Rainy cloud on scale set diagnostics

- Applicable: This issue applies to all supported releases.
- Cause: The virtual machine scale set overview page shows an empty chart. Clicking on the empty chart opens a "rainy cloud" blade. This is the chart for scale set diagnostic information, such as CPU percentage, and is not a feature supported in the current Azure Stack build.
- Remediation: None.
- Occurrence: Common

### Virtual machine diagnostic settings blade

- Applicable: This issue applies to all supported releases.    
- Cause: The virtual machine diagnostic settings blade has a **Sink** tab, which asks for an **Application Insight Account**. This is the result of a new blade and is not yet supported in Azure Stack.
- Remediation: None.
- Occurrence: Common
::: moniker-end

::: moniker range="azs-1907"
## 1907 archived known issues

This article lists known issues in releases of Azure Stack. The list is updated as new issues are identified.

To access known issues for a different version, use the version selector dropdown above the table of contents on the left.

> [!IMPORTANT]  
> Review this section before applying the update.

> [!IMPORTANT]  
> If your Azure Stack instance is behind by more than two updates, it's considered out of compliance. You must [update to at least the minimum supported version to receive support](../azure-stack-servicing-policy.md#keep-your-system-under-support).

## 1907 update process

- Applicable: This issue applies to all supported releases.
- Cause: When attempting to install the 1907 Azure Stack update, the status for the update might fail and change state to **PreparationFailed**. This is caused by the update resource provider (URP) being unable to properly transfer the files from the storage container to an internal infrastructure share for processing.
- Remediation: Starting with version 1901 (1.1901.0.95), you can work around this issue by clicking **Update now** again (not **Resume**). The URP then cleans up the files from the previous attempt, and restarts the download. If the problem persists, we recommend manually uploading the update package by following the [Import and install updates section](../azure-stack-apply-updates.md).
- Occurrence: Common

## Portal

### Administrative subscriptions

- Applicable: This issue applies to all supported releases.
- Cause: The two administrative subscriptions that were introduced with version 1804 should not be used. The subscription types are **Metering** subscription, and **Consumption** subscription.
- Remediation: If you have resources running on these two subscriptions, recreate them in user subscriptions.
- Occurrence: Common

### Subscriptions Properties blade

- Applicable: This issue applies to all supported releases.
- Cause: In the administrator portal, the **Properties** blade for subscriptions does not load correctly
- Remediation: You can view these subscription properties in the **Essentials** pane of the **Subscriptions Overview** blade.
- Occurrence: Common

### Subscription permissions

- Applicable: This issue applies to all supported releases.
- Cause: You cannot view permissions to your subscription using the Azure Stack portals.
- Remediation: Use [PowerShell to verify permissions](/powershell/module/azurerm.resources/get-azurermroleassignment).
- Occurrence: Common

### Storage account settings

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the storage account **Configuration** blade shows an option to change **security transfer type**. The feature is currently not supported in Azure Stack.
- Occurrence: Common

### Upload blob

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, when you try to upload a blob using the **OAuth(preview)** option, the task fails with an error message.
- Remediation: Upload the blob using the SAS option.
- Occurrence: Common

## Networking

### Service endpoints

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **Virtual Network** blade shows an option to use **Service Endpoints**. This feature is currently not supported in Azure Stack.
- Occurrence: Common

### Network interface

- Applicable: This issue applies to all supported releases.
- Cause: A new network interface cannot be added to a VM that is in a **running** state.
- Remediation: Stop the virtual machine before adding/removing a network interface.
- Occurrence: Common

### Virtual Network Gateway

#### Alerts

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **Virtual Network Gateway** blade shows an option to use **Alerts**. This feature is currently not supported in Azure Stack.
- Occurrence: Common

#### Active-Active

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, while creating, and in the resource menu of **Virtual Network Gateway**, you will see an option to enable **Active-Active** configuration. This feature is currently not supported in Azure Stack.
- Occurrence: Common

#### VPN troubleshooter

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **Connections** blade shows a feature called **VPN Troubleshooter**. This feature is currently not supported in Azure Stack.
- Occurrence: Common

### Network Connection Type

- Applicable: This issue applies to any 1906 or 1907 environment. 
- Cause: In the user portal, the **AddConnection** blade shows an option to use **VNet-to-VNet**. This feature is currently not supported in Azure Stack. 
- Occurrence: Common 

#### Documentation

- Applicable: This issue applies to all supported releases.
- Cause: The documentation links in the overview page of Virtual Network gateway link to Azure-specific documentation instead of Azure Stack. Use the following links for the Azure Stack documentation:

  - [Gateway SKUs](../../user/azure-stack-vpn-gateway-about-vpn-gateways.md#gateway-skus)
  - [Highly Available Connections](../../user/azure-stack-vpn-gateway-about-vpn-gateways.md#gateway-availability)
  - [Configure BGP on Azure Stack](../../user/azure-stack-vpn-gateway-settings.md#gateway-requirements)
  - [ExpressRoute circuits](../azure-stack-connect-expressroute.md)
  - [Specify custom IPsec/IKE policies](../../user/azure-stack-vpn-gateway-settings.md#ipsecike-parameters)

## Compute

### VM boot diagnostics

- Applicable: This issue applies to all supported releases.
- Cause: When creating a new Windows virtual machine (VM), the following error may be displayed:
**Failed to start virtual machine 'vm-name'. Error: Failed to update serial output settings for VM 'vm-name'**. The error occurs if you enable boot diagnostics on a VM, but delete your boot diagnostics storage account.
- Remediation: Recreate the storage account with the same name you used previously.
- Occurrence: Common

### Virtual machine scale set

#### Create failures during patch and update on 4-node Azure Stack environments

- Applicable: This issue applies to all supported releases.
- Cause: Creating VMs in an availability set of 3 fault domains and creating a virtual machine scale set instance fails with a **FabricVmPlacementErrorUnsupportedFaultDomainSize** error during the update process on a 4-node Azure Stack environment.
- Remediation: You can create single VMs in an availability set with 2 fault domains successfully. However, scale set instance creation is still not available during the update process on a 4-node Azure Stack.

### Ubuntu SSH access

- Applicable: This issue applies to all supported releases.
- Cause: An Ubuntu 18.04 VM created with SSH authorization enabled does not allow you to use the SSH keys to sign in.
- Remediation: Use VM access for the Linux extension to implement SSH keys after provisioning, or use password-based authentication.
- Occurrence: Common

### Virtual machine scale set reset password does not work

- Applicable: This issue applies to the 1906 and 1907 releases.
- Cause: A new reset password blade appears in the scale set UI, but Azure Stack does not support resetting password on a scale set yet.
- Remediation: None.
- Occurrence: Common

### Rainy cloud on scale set diagnostics

- Applicable: This issue applies to the 1906 and 1907 releases.
- Cause: The virtual machine scale set overview page shows an empty chart. Clicking on the empty chart opens a "rainy cloud" blade. This is the chart for scale set diagnostic information, such as CPU percentage, and is not a feature supported in the current Azure Stack build.
- Remediation: None.
- Occurrence: Common

### Virtual machine diagnostic settings blade

- Applicable: This issue applies to the 1906 and 1907 releases.    
- Cause: The virtual machine diagnostic settings blade has a **Sink** tab, which asks for an **Application Insight Account**. This is the result of a new blade and is not yet supported in Azure Stack.
- Remediation: None.
- Occurrence: Common
::: moniker-end

::: moniker range="azs-1906"
## 1906 archived known issues

This article lists known issues in releases of Azure Stack. The list is updated as new issues are identified.

To access known issues for a different version, use the version selector dropdown above the table of contents on the left.

> [!IMPORTANT]  
> Review this section before applying the update.

> [!IMPORTANT]  
> If your Azure Stack instance is behind by more than two updates, it's considered out of compliance. You must [update to at least the minimum supported version to receive support](../azure-stack-servicing-policy.md#keep-your-system-under-support). 

## 1906 update process

- Applicable: This issue applies to all supported releases.
- Cause: When attempting to install the 1906 Azure Stack update, the status for the update might fail and change state to **PreparationFailed**. This is caused by the update resource provider (URP) being unable to properly transfer the files from the storage container to an internal infrastructure share for processing. 
- Remediation: Starting with version 1901 (1.1901.0.95), you can work around this issue by clicking **Update now** again (not **Resume**). The URP then cleans up the files from the previous attempt, and restarts the download. If the problem persists, we recommend manually uploading the update package by following the [Import and install updates section](../azure-stack-apply-updates.md).
- Occurrence: Common

## Portal

### Administrative subscriptions

- Applicable: This issue applies to all supported releases.
- Cause: The two administrative subscriptions that were introduced with version 1804 should not be used. The subscription types are **Metering** subscription, and **Consumption** subscription.
- Remediation: If you have resources running on these two subscriptions, recreate them in user subscriptions.
- Occurrence: Common

### Subscription resources

- Applicable: This issue applies to all supported releases.
- Cause: Deleting user subscriptions results in orphaned resources.
- Remediation: First delete user resources or the entire resource group, and then delete the user subscriptions.
- Occurrence: Common

### Subscription permissions

- Applicable: This issue applies to all supported releases.
- Cause: You cannot view permissions to your subscription using the Azure Stack portals.
- Remediation: Use [PowerShell to verify permissions](/powershell/module/azurerm.resources/get-azurermroleassignment).
- Occurrence: Common

### Subscriptions Properties blade
- Applicable: This issue applies to all supported releases.
- Cause: In the administrator portal, the **Properties** blade for Subscriptions does not load correctly
- Remediation: You can view these subscriptions properties in the Essentials pane of the Subscriptions Overview blade
- Occurrence: Common

### Storage account settings

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the storage account **Configuration** blade shows an option to change **security transfer type**. The feature is currently not supported in Azure Stack.
- Occurrence: Common

### Upload blob

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, when you try to upload a blob using the **OAuth(preview)** option, the task fails with an error message.
- Remediation: Upload the blob using the SAS option.
- Occurrence: Common

### Update

- Applicable: This issue applies to the 1906 release.
- Cause: In the operator portal, update status for the hotfix shows an incorrect state for the update. Initial state indicates that the update failed to install, even though it is still in progress.
- Remediation: Refresh the portal and the state will update to "in progress."
- Occurrence: Intermittent

## Networking

### Service endpoints

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **Virtual Network** blade shows an option to use **Service Endpoints**. This feature is currently not supported in Azure Stack.
- Occurrence: Common

### Network interface

- Applicable: This issue applies to all supported releases.
- Cause: A new network interface cannot be added to a VM that is in a **running** state.
- Remediation: Stop the virtual machine before adding/removing a network interface.
- Occurrence: Common

### Virtual Network Gateway

#### Alerts

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **Virtual Network Gateway** blade shows an option to use **Alerts**. This feature is currently not supported in Azure Stack.
- Occurrence: Common

#### Active-Active

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, while creating, and in the resource menu of **Virtual Network Gateway**, you will see an option to enable **Active-Active** configuration. This feature is currently not supported in Azure Stack.
- Occurrence: Common

#### VPN troubleshooter

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **Connections** blade shows a feature called **VPN Troubleshooter**. This feature is currently not supported in Azure Stack.
- Occurrence: Common

#### Documentation

- Applicable: This issue applies to all supported releases.
- Cause: The documentation links in the overview page of Virtual Network gateway link to Azure-specific documentation instead of Azure Stack. Please use the following links for the Azure Stack documentation:

  - [Gateway SKUs](../../user/azure-stack-vpn-gateway-about-vpn-gateways.md#gateway-skus)
  - [Highly Available Connections](../../user/azure-stack-vpn-gateway-about-vpn-gateways.md#gateway-availability)
  - [Configure BGP on Azure Stack](../../user/azure-stack-vpn-gateway-settings.md#gateway-requirements)
  - [ExpressRoute circuits](../azure-stack-connect-expressroute.md)
  - [Specify custom IPsec/IKE policies](../../user/azure-stack-vpn-gateway-settings.md#ipsecike-parameters)

### Load balancer

#### Add backend pool

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, if you attempt to add a **Backend Pool** to a **Load Balancer**, the operation fails with the error message **failed to update Load Balancer...**.
- Remediation: Use PowerShell, CLI or a Resource Manager template to associate the backend pool with a load balancer resource.
- Occurrence: Common

#### Create inbound NAT

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, if you attempt to create an **Inbound NAT Rule** for a **Load Balancer**, the operation fails with the error message **Failed to update Load Balancer...**.
- Remediation: Use PowerShell, CLI or a Resource Manager template to associate the backend pool with a load balancer resource.
- Occurrence: Common

## Compute

### VM boot diagnostics

- Applicable: This issue applies to all supported releases.
- Cause: When creating a new Windows virtual machine (VM), the following error may be displayed:
**Failed to start virtual machine 'vm-name'. Error: Failed to update serial output settings for VM 'vm-name'**. The error occurs if you enable boot diagnostics on a VM, but delete your boot diagnostics storage account.
- Remediation: Recreate the storage account with the same name you used previously.
- Occurrence: Common

### Virtual machine scale set


#### Create failures during patch and update on 4-node Azure Stack environments

- Applicable: This issue applies to all supported releases.
- Cause: Creating VMs in an availability set of 3 fault domains and creating a virtual machine scale set instance fails with a **FabricVmPlacementErrorUnsupportedFaultDomainSize** error during the update process on a 4-node Azure Stack environment.
- Remediation: You can create single VMs in an availability set with 2 fault domains successfully. However, scale set instance creation is still not available during the update process on a 4-node Azure Stack.

### Ubuntu SSH access

- Applicable: This issue applies to all supported releases.
- Cause: An Ubuntu 18.04 VM created with SSH authorization enabled does not allow you to use the SSH keys to sign in.
- Remediation: Use VM access for the Linux extension to implement SSH keys after provisioning, or use password-based authentication.
- Occurrence: Common

### Virtual machine scale set reset password does not work

- Applicable: This issue applies to the 1906 release.
- Cause: A new reset password blade appears in the scale set UI, but Azure Stack does not support resetting password on a scale set yet.
- Remediation: None.
- Occurrence: Common

### Rainy cloud on scale set diagnostics

- Applicable: This issue applies to the 1906 release.
- Cause: The virtual machine scale set overview page shows an empty chart. Clicking on the empty chart opens a "rainy cloud" blade. This is the chart for scale set diagnostic information, such as CPU percentage, and is not a feature supported in the current Azure Stack build.
- Remediation: None.
- Occurrence: Common

### Virtual machine diagnostic settings blade

- Applicable: This issue applies to the 1906 release.
- Cause: The virtual machine diagnostic settings blade has a **Sink** tab, which asks for an **Application Insight Account**. This is the result of a new blade and is not yet supported in Azure Stack.
- Remediation: None.
- Occurrence: Common
::: moniker-end

::: moniker range="azs-1905"
## 1905 archived known issues

This article lists known issues in the 1905 release of Azure Stack. The list is updated as new issues are identified.

> [!IMPORTANT]  
> Review this section before applying the update.

## Update process

### Host node update prerequisite failure

- Applicable: This issue applies to the 1905 update.
- Cause: When attempting to install the 1905 Azure Stack update, the status for the update might fail due to **Host Node Update Prerequisite**. This is generally caused by a host node having insufficient free disk space.
- Remediation: Contact Azure Stack support to receive assistance clearing disk space on the host node.
- Occurrence: Uncommon

### Preparation failed

- Applicable: This issue applies to all supported releases.
- Cause: When attempting to install the 1905 Azure Stack update, the status for the update might fail and change state to **PreparationFailed**. This is caused by the update resource provider (URP) being unable to properly transfer the files from the storage container to an internal infrastructure share for processing. The 1905 update package is larger than previous update packages which may make this issue more likely to occur.
- Remediation: Starting with version 1901 (1.1901.0.95), you can work around this issue by clicking **Update now** again (not **Resume**). The URP then cleans up the files from the previous attempt, and restarts the download. If the problem persists, we recommend manually uploading the update package by following the [Import and install updates section](../azure-stack-apply-updates.md).
- Occurrence: Common

## Portal

### Subscription resources

- Applicable: This issue applies to all supported releases.
- Cause: Deleting user subscriptions results in orphaned resources.
- Remediation: First delete user resources or the entire resource group, and then delete the user subscriptions.
- Occurrence: Common

### Subscription permissions

- Applicable: This issue applies to all supported releases.
- Cause: You cannot view permissions to your subscription using the Azure Stack portals.
- Remediation: Use [PowerShell to verify permissions](/powershell/module/azurerm.resources/get-azurermroleassignment).
- Occurrence: Common

### Marketplace management

- Applicable: This issue applies to 1904 and 1905
- Cause: The marketplace management screen is not visible when you sign in to the administrator portal.
- Remediation: Refresh the browser or go to **Settings** and select the option **Reset to default settings**.
- Occurrence: Intermittent

### Docker extension

- Applicable: This issue applies to all supported releases.
- Cause: In both the administrator and user portals, if you search for **Docker**, the item is incorrectly returned. It is not available in Azure Stack. If you try to create it, an error is displayed.
- Remediation: No mitigation.
- Occurrence: Common

### Upload blob

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, when you try to upload a blob using the **OAuth(preview)** option, the task fails with an error message.
- Remediation: Upload the blob using the SAS option.
- Occurrence: Common

### Template

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the template deployment UI does not populate parameters for the template names beginning with "_" (the underscore character).
- Remediation: Remove the "_" (underscore character) from the template name.
- Occurrence: Common

## Networking

### Load balancer

#### Add backend pool

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, if you attempt to add a **Backend Pool** to a **Load Balancer**, the operation fails with the error message **failed to update Load Balancer...**.
- Remediation: Use PowerShell, CLI or a Resource Manager template to associate the backend pool with a load balancer resource.
- Occurrence: Common

#### Create inbound NAT

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, if you attempt to create an **Inbound NAT Rule** for a **Load Balancer**, the operation fails with the error message **Failed to update Load Balancer...**.
- Remediation: Use PowerShell, CLI or a Resource Manager template to associate the backend pool with a load balancer resource.
- Occurrence: Common

#### Create load balancer

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **Create Load Balancer** window shows an option to create a **Standard** load balancer SKU. This option is not supported in Azure Stack.
- Remediation: Use the **Basic** load balancer options instead.
- Occurrence: Common

### Public IP address

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **Create Public IP Address** window shows an option to create a **Standard** SKU. The **Standard** SKU is not supported in Azure Stack.
- Remediation: Use the **Basic** SKU for public IP address.
- Occurrence: Common

## Compute

### VM boot diagnostics

- Applicable: This issue applies to all supported releases.
- Cause: When creating a new Windows virtual machine (VM), the following error may be displayed:
**Failed to start virtual machine 'vm-name'. Error: Failed to update serial output settings for VM 'vm-name'**.
The error occurs if you enable boot diagnostics on a VM, but delete your boot diagnostics storage account.
- Remediation: Recreate the storage account with the same name you used previously.
- Occurrence: Common

### VM resize

- Applicable: This issue applies to the 1905 release.
- Cause: Unable to successfully resize a managed disk VM. Attempting to resize the VM generates an error with "code": "InternalOperationError",
  "message": "An internal error occurred in the operation."
- Remediation: We are working to remediate this in the next release. Currently, you must recreate the VM with the new VM size.
- Occurrence: Common

### Virtual machine scale set

#### CentOS

- Applicable: This issue applies to all supported releases.
- Cause: The virtual machine scale set creation experience provides CentOS-based 7.2 as an option for deployment. CentOS 7.2 is not available on Azure Stack Marketplace which will cause deployment failures calling out that the image is not found.
- Remediation: Select another operating system for your deployment, or use an Azure Resource Manager template specifying another CentOS image that has been downloaded prior to deployment from the marketplace by the operator.
- Occurrence: Common

#### Remove scale set

- Applicable: This issue applies to all supported releases.
- Cause: You cannot remove a scale set from the **Virtual machine scale sets** blade.
- Remediation: Select the scale set that you want to remove, then click the **Delete** button from the **Overview** pane.
- Occurrence: Common

#### Create failures during patch and update on 4-node Azure Stack environments

- Applicable: This issue applies to all supported releases.
- Cause: Creating VMs in an availability set of 3 fault domains and creating a virtual machine scale set instance fails with a **FabricVmPlacementErrorUnsupportedFaultDomainSize** error during the update process on a 4-node Azure Stack environment.
- Remediation: You can create single VMs in an availability set with 2 fault domains successfully. However, scale set instance creation is still not available during the update process on a 4-node Azure Stack.

#### Scale set instance view blade doesn't load

- Applicable: This issue applies to 1904 and 1905 release.
- Cause: The instance view blade of a virtual machine scale set located at Azure Stack portal -> Dashboard -> Virtual machine scale sets -> AnyScaleSet - Instances -> AnyScaleSetInstance fails to load, and displays a crying cloud image.
- Remediation: There is currently no remediation and we are working on a fix. Until then, please use the CLI command `az vmss get-instance-view` to get the instance view of a scale set.

### Ubuntu SSH access

- Applicable: This issue applies to all supported releases.
- Cause: An Ubuntu 18.04 VM created with SSH authorization enabled does not allow you to use the SSH keys to sign in.
- Remediation: Use VM access for the Linux extension to implement SSH keys after provisioning, or use password-based authentication.
- Occurrence: Common

<!-- ## Storage -->
<!-- ## SQL and MySQL-->
<!-- ## App Service -->
<!-- ## Usage -->
<!-- ### Identity -->
<!-- ### Marketplace -->

## Next steps

- [Review update activity checklist](../release-notes-checklist.md)
- [Review list of security updates](../release-notes-security-updates.md)
::: moniker-end

::: moniker range="azs-1904"
## 1904 archived known issues

This article lists known issues in the 1904 release of Azure Stack. The list is updated as new issues are identified.

> [!IMPORTANT]  
> Review this section before applying the update.

## Update process

- Applicable: This issue applies to all supported releases.
- Cause: When attempting to install an Azure Stack update, the status for the update might fail and change state to **PreparationFailed**. This is caused by the update resource provider (URP) being unable to properly transfer the files from the storage container to an internal infrastructure share for processing.
- Remediation: Starting with version 1901 (1.1901.0.95), you can work around this issue by clicking **Update now** again (not **Resume**). The URP then cleans up the files from the previous attempt, and starts the download again.
- Occurrence: Common

## Portal

### Administrative subscriptions

- Applicable: This issue applies to all supported releases.
- Cause: The two administrative subscriptions that were introduced with version 1804 should not be used. The subscription types are **Metering** subscription, and **Consumption** subscription.
- Remediation: If you have resources running on these two subscriptions, recreate them in user subscriptions.
- Occurrence: Common

### Subscription resources

- Applicable: This issue applies to all supported releases.
- Cause: Deleting user subscriptions results in orphaned resources.
- Remediation: First delete user resources or the entire resource group, and then delete the user subscriptions.
- Occurrence: Common

### Subscription permissions

- Applicable: This issue applies to all supported releases.
- Cause: You cannot view permissions to your subscription using the Azure Stack portals.
- Remediation: Use [PowerShell to verify permissions](/powershell/module/azurerm.resources/get-azurermroleassignment).
- Occurrence: Common

### Docker extension

- Applicable: This issue applies to all supported releases.
- Cause: In both the administrator and user portals, if you search for **Docker**, the item is incorrectly returned. It is not available in Azure Stack. If you try to create it, an error is displayed.
- Remediation: No mitigation.
- Occurrence: Common

### Marketplace management

- Applicable: This is a new issue with release 1904.
- Cause: The marketplace management screen is not visible when you sign in to the administrator portal.
- Remediation: Refresh the browser.
- Occurrence: Intermittent

### Marketplace management

- Applicable: This issue applies to 1904.
- Cause: When you filter results in the **Add from Azure** blade in the Marketplace management tab in the administrator portal, you may see incorrect filtered results.
- Remediation: Sort results by the Name column and the results will be corrected.
- Occurrence: Intermittent

### Marketplace management

- Applicable: This issue applies to 1904.
- Cause: When you filter results in Marketplace management in the administrator portal, you will see duplicated publisher names under the publisher drop-down. 
- Remediation: Select all the duplicates to have the correct list of all the Marketplace products that are available under that publisher.
- Occurrence: Intermittent

### Docker extension

- Applicable: This issue applies to all supported releases.
- Cause: In both the administrator and user portals, if you search for **Docker**, the item is incorrectly returned. It is not available in Azure Stack. If you try to create it, an error is displayed.
- Remediation: No mitigation.
- Occurrence: Common

### Upload blob

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, when you try to upload a blob using the OAuth(preview) option, the task fails with an error message.
- Remediation: Upload the blob using the SAS option.
- Occurrence: Common

### Template

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the template deployment UI does not populate parameters for the template names beginning with "_" (the underscore character).
- Remediation: Remove the "_" (underscore character) from the template name.
- Occurrence: Common

## Networking

### Load balancer

#### Add backend pool

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, if you attempt to add a **Backend Pool** to a **Load Balancer**, the operation fails with the error message **Failed to update Load Balancer...**.
- Remediation: Use PowerShell, CLI, or an Azure Resource Manager template to associate the backend pool with a load balancer resource.
- Occurrence: Common

#### Create inbound NAT

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, if you attempt to create an **Inbound NAT Rule** for a **Load Balancer**, the operation fails with the error message **Failed to update Load Balancer...**.
- Remediation: Use PowerShell, CLI, or an Azure Resource Manager template to associate the backend pool with a load balancer resource.
- Occurrence: Common

#### Create load balancer

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **Create Load Balancer** window shows an option to create a **Standard** load balancer SKU. This option is not supported in Azure Stack.
- Remediation: Use the Basic load balancer options instead.
- Occurrence: Common

#### Public IP address

- Applicable: This issue applies to all supported releases.
- Cause: In the user portal, the **Create Public IP Address** window shows an option to create a **Standard** SKU. The **Standard** SKU is not supported in Azure Stack.
- Remediation: Use the **Basic** SKU instead for public IP addresses.
- Occurrence: Common

## Compute

### VM boot diagnostics

- Applicable: This issue applies to all supported releases.
- Cause: When creating a new Windows Virtual Machine (VM), the following error may be displayed:
**Failed to start virtual machine 'vm-name'. Error: Failed to update serial output settings for VM 'vm-name'**.
The error occurs if you enable boot diagnostics on a VM, but delete your boot diagnostics storage account.
- Remediation: Recreate the storage account with the same name you used previously.
- Occurrence: Common

### Virtual machine scale set

#### CentOS

- Applicable: This issue applies to all supported releases.
- Cause: The virtual machine scale set creation experience provides CentOS-based 7.2 as an option for deployment. CentOS 7.2 is not available on Azure Stack Marketplace which will cause deployment failures calling out that the image is not found.
- Remediation: Select another operating system for your deployment, or use an Azure Resource Manager template specifying another CentOS image that has been downloaded prior to deployment from the marketplace by the operator.
- Occurrence: Common

#### Remove scale set

- Applicable: This issue applies to all supported releases.
- Cause: You cannot remove a scale set from the **Virtual Machine Scale Sets** blade.
- Remediation: Select the scale set that you want to remove, then click the **Delete** button from the **Overview** pane.
- Occurrence: Common

#### Create failures during patch and update on 4-node Azure Stack environments

- Applicable: This issue applies to all supported releases.
- Cause: Creating VMs in an availability set of 3 fault domains and creating a virtual machine scale set instance fails with a **FabricVmPlacementErrorUnsupportedFaultDomainSize** error during the update process on a 4-node Azure Stack environment.
- Remediation: You can create single VMs in an availability set with 2 fault domains successfully. However, scale set instance creation is still not available during the update process on a 4-node Azure Stack.

### Ubuntu SSH access

- Applicable: This issue applies to all supported releases.
- Cause: An Ubuntu 18.04 VM created with SSH authorization enabled does not allow you to use the SSH keys to sign in.
- Remediation: Use VM access for the Linux extension to implement SSH keys after provisioning, or use password-based authentication.
- Occurrence: Common

### Compute host agent alert

- Applicable: This is a new issue with release 1904.
- Cause: A **Compute host agent** warning appears after restarting a node in the scale unit. The restart changes the default startup setting for the compute host agent service. This alert looks similar to the following example:

   ```shell
   NAME  
   Compute Host Agent is not responding to calls.
   SEVERITY  
   Warning
   STATE  
   Active
   CREATED TIME  
   5/16/2019, 10:08:23 AM
   UPDATED TIME  
   5/22/2019, 12:27:27 PM
   COMPONENT  
   M#####-NODE02
   DESCRIPTION  
   Could not communicate with the Compute Host Agent running on node: M#####-NODE02
   REMEDIATION  
   Please disable Compute Host Agent feature flag and collect logs for further diagnosis.
   ```

- Remediation:
  - This alert can be ignored. The agent not responding does not have any impact on operator and user operations or user applications. The alert will reappear after 24 hours if it is closed manually.
  - The issue is fixed in the latest [Azure Stack hotfix for 1904](https://support.microsoft.com/help/4505688).
- Occurrence: Common

### Virtual machine scale set instance view

- Applicable: This issue applies to the 1904 and 1905 releases.
- Cause: The instance view blade of a scale set located on the Azure Stack portal, in **Dashboard** > **Virtual machine scale sets** > **AnyScaleSet - Instances** > **AnyScaleSetInstance** fails to load.
- Remediation: There is currently no remediation and we are working on a fix. Until then, please use the CLI cmdlet `az vmss get-instance-view` to get the instance view of a virtual machine scale set.

### User image service
- Applicable: This issue applies to all supported releases.
- Cause: Failed user image creation will put the user image service into a bad state. User image creation and deletion operations will start to fail. User image deletion may fail with error: "Error: An internal disk management error occurred."
- Remediation: No mitigation. Open a support ticket with Microsoft.

## Storage

- Applicable: This issue applies to all supported releases.
- Cause: [ConvertTo-AzureRmVMManagedDisk](/powershell/module/azurerm.compute/convertto-azurermvmmanageddisk) is not supported in Azure Stack and results in creating a disk with **$null** ID. This prevents you from performing operations on the VM, such as start and stop. The disk does not appear in the UI, nor does it appear via the API. The VM at that point cannot be repaired and must be deleted.
- Remediation: To convert your disks correctly, follow the [convert to managed disks guide](../../user/azure-stack-managed-disk-considerations.md#convert-to-managed-disks).

## App Service

- Tenants must register the storage resource provider before creating their first Azure Function in the subscription.
- Some tenant portal user experiences are broken due to an incompatibility with the portal framework in 1903; principally, the UX for deployment slots, testing in production and site extensions. To work around this issue, use the [Azure App Service PowerShell module](/azure/app-service/deploy-staging-slots#automate-with-powershell) or the [Azure CLI](/cli/azure/webapp/deployment/slot?view=azure-cli-latest&preserve-view=true). The portal experience will be restored by upgrading your deployment of [Azure App Service on Azure Stack to 1.6 (Update 6)](../azure-stack-app-service-release-notes-update-six.md).

## Next steps

- [Review update activity checklist](../release-notes-checklist.md)
- [Review list of security updates](../release-notes-security-updates.md)
::: moniker-end

::: moniker range="azs-1903"
## 1903 archived known issues
::: moniker-end

::: moniker range="azs-1902"
## 1902 archived known issues
::: moniker-end

::: moniker range="azs-1901"
## 1901 archived known issues
::: moniker-end

::: moniker range="azs-1811"
## 1811 archived known issues
::: moniker-end

::: moniker range="azs-1809"
## 1809 archived known issues
::: moniker-end

::: moniker range="azs-1808"
## 1808 archived known issues
::: moniker-end

::: moniker range="azs-1807"
## 1807 archived known issues
::: moniker-end

::: moniker range="azs-1805"
## 1805 archived known issues
::: moniker-end

::: moniker range="azs-1804"
## 1804 archived known issues
::: moniker-end

::: moniker range="azs-1803"
## 1803 archived known issues
::: moniker-end

::: moniker range="azs-1802"
## 1802 archived known issues
::: moniker-end

::: moniker range="<azs-1904"
Known issues for this release are combined with the [archived release notes](release-notes.md)
::: moniker-end