---
# required metadata
title: Resize a single Cloud PC
titleSuffix:
description: Learn how to resize a single Cloud PC by using Microsoft Intune.
keywords:
author: ErikjeMS  
ms.author: erikje
manager: dougeby
ms.date: 04/28/2025
ms.topic: overview
ms.service: windows-365
ms.subservice: windows-365-enterprise
ms.localizationpriority: high
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:

ms.reviewer: abpineda
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure; get-started
ms.collection:
- M365-identity-device-management
- tier2
---

# Resize a single Cloud PC

You can use the **Resize** remote action to resize a single Cloud PC that was provisioned with a direct assigned license or a group-based licensed.

For more information about resizing Cloud PCs in bulk, see [Resize Cloud PCs in bulk](resize-cloud-pc-bulk.md).

For more information about resizing, see [Cloud PC resizing overview](resize-cloud-pc.md).

[!INCLUDE [Resize a Cloud PC requirements](../includes/resize-requirements.md)]

## Resize a single Cloud PC provisioned with a direct assigned license

When resizing Cloud PCs provisioned through direct assigned licenses the Windows 365 service automatically takes care of:

- Unassigning the original license.
- Assigning the new license on behalf of the admin.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** > **All Devices** > choose a device > **Resize**.
![Screenshot of resize a Cloud PC.](./media/resize-cloud-pc/resize.png)
2. Under **Resize**, there's a list of the sizes that you can upgrade or downsize to based on the licenses available in your inventory. You can upgrade/downgrade a Cloud PC’s RAM and vCPU. You can only upgrade the OS disk storage. If you're downgrading a user’s Cloud PC, options with lower storage are grayed out. Select one of the available options.
3. Select **Resize**.

If there are available licenses, the resizing starts.

## Resize a single Cloud PC provisioned with a group-based license

1. Create a new target Microsoft Entra group. Add the users from the source Microsoft Entra group that you want to resize. Alternately, you can use existing Microsoft Entra groups if you're mapping the groups to individual Windows 365 license types.
2. Assign the existing provisioning policy targeting the original source Microsoft Entra group to the new target Microsoft Entra group. You only need to do this step if you don't have a discrete Microsoft Entra group for your provisioning policy assignment. If you have discrete Microsoft Entra groups to manage your provisioning policy assignments, you can omit this step.
3. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** > **All Devices** > choose the device that you want added to the Microsoft Entra target group > **Resize**.
![Screenshot of resize a Cloud PC.](./media/resize-cloud-pc/resize.png)
4. A list is displayed with all the possible SKUs that you can upgrade or downsize to based on the licenses that you have available in your inventory. You can upgrade/downgrade a Cloud PC’s RAM and vCPU. You can only upgrade the OS disk storage. If you're downsizing a user’s Cloud PC, options with lower storage are grayed out. Select one of the available options.
5. Select **Resize**.
6. The user’s Cloud PC is placed in the **Resize pending license** state as can be seen in the Windows 365 provisioning blade.
7. Select **Users** > search for the user name assigned to the Cloud PC and select it > **Groups**.
8. To retrieve the old license, remove the users from the original source Microsoft Entra group. If you don’t perform this step, a new Cloud PC will be provisioned with the original source license after you assign the target license.
    - When using Microsoft Entra ID hybrid in your environment, after removing the user from the original group, you must wait until Microsoft Entra Connect synchronizes your on-premises Active Directory with your Microsoft Entra ID. This synchornization can take up to 30 minutes. Then you can add the user to the new group.
9. Assign the target license to the new target Microsoft Entra group. The resizing process now begins.

<!-- ########################## -->
## Next steps

For more information on Cloud PC sizes, see [Cloud PC size recommendations](cloud-pc-size-recommendations.md).
