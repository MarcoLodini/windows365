---
# required metadata
title: Resize multiple Cloud PCs
titleSuffix:
description: Learn how to resize multiple Cloud PCs by using Microsoft Intune.
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

# Resize Cloud PCs in bulk

You can resize Cloud PCs in bulk using Microsoft Intune.

Resizing in bulk can have large scale impact. Before resizing a large group of Cloud PCs, try resizing a small group. This step helps familiarize you with the process.

Up to 5,000 Cloud PCs can be resized at a time.

For more information about resizing a single Cloud PC, see [Resize a single Cloud PCs](resize-cloud-pc-single.md).

For more information about resizing, see [Cloud PC resizing overview](resize-cloud-pc.md).

[!INCLUDE [Resize a Cloud PC requirements](../includes/resize-requirements.md)]

## Bulk resize Cloud PCs originally provisioned with directly assigned licenses

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** > **All Devices** > **Bulk device actions** > **OS (Windows)** > **Select device type (Cloud PCs)** > **Device action (Resize)**.
2. On the **Basics** page, select the **Source size** for the Cloud PCs to be resized.
3. Select the **Target size** for the resized Cloud PCs > **Next**.
4. On the **Devices** page, choose **Select individual devices across your environment** > **Next**.
5. Under **Select devices**, choose the devices that you want to resize > **Next**.
6. On the **Review + create** page, select **Create**.

## Bulk resize Cloud PCs originally provisioned with group-based licenses

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** > **All Devices** > **Bulk device actions** > **OS (Windows)** > **Select device type (Cloud PCs)** > **Device action (Resize)**.
2. On the **Basics** page, select the **Source size** for the Cloud PCs to be resized.
3. Select the **Target size** for the resized Cloud PCs > **Next**.
4. On the **Devices** page, choose **Apply this action to the devices registered to its group members** > **Next**.
5. Under **Select groups to include**, choose the groups containing the users who own the devices that you want to resize > **Next**.
6. On the **Review + create** page, select **Create**. The user’s Cloud PC is placed in the **Resize pending license** state as can be seen in the Windows 365 provisioning blade.
7. Select **Groups** > select the group that your changing > **Licenses** > select the old license > **Remove license** > **Yes** > **Save**. Repeat this step for each group that you want to change.
8. Select **Assignments** > select the license that you want to resize the Cloud PCs to > **Save**. The users' Cloud PC starts resizing, which you can check in the Windows 365 provisioning blade.

## Bulk resize a subset of Cloud PCs originally provisioned using group-based licenses

1. Create a new target Microsoft Entra group. Add the users from the source Microsoft Entra group that you want to resize. Alternately, you can use existing Microsoft Entra groups if you're mapping the groups to individual Windows 365 license types.
2. Assign the existing provisioning policy targeting the original source Microsoft Entra group to the new target Microsoft Entra group. You only need to do this step if you don't have a discrete Microsoft Entra group for your provisioning policy assignment. If you have discrete Microsoft Entra groups to manage your provisioning policy assignments, you can omit this step.
3. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** > **All Devices** > **Bulk device actions** > **OS (Windows)** > **Select device type (Cloud PCs)** > **Device action (Resize)**.
4. On the **Basics** page, select the **Source size** for the Cloud PCs to be resized.
5. Select the **Target size** for the resized Cloud PCs > **Next**.
6. On the **Devices** page, choose **Apply this action to the devices registered to its group members** > **Next**.
7. Under **Select groups to include**, choose the groups containing the users who own the devices that you want to resize > **Next**.
8. On the **Review + create** page, select **Create**. The user’s Cloud PC is placed in the **Resize pending license** state as can be seen in the Windows 365 provisioning blade.
9. To retrieve the old license, remove the users from the original source Microsoft Entra group. If you don’t perform this step, a new Cloud PC is provisioned with the original source license after you assign the target license.
    - When using Microsoft Entra ID hybrid in your environment, after removing the user from the original group, you must wait until Microsoft Entra Connect synchronizes your on-premises Active Directory with your Microsoft Entra ID. This synchronization can take up to 30 minutes. Then you can add the user to the new group.
10. Assign the target license to the new target Microsoft Entra group. The resizing process now begins.

<!-- ########################## -->
## Next steps

For more information on Cloud PC sizes, see [Cloud PC size recommendations](cloud-pc-size-recommendations.md).
