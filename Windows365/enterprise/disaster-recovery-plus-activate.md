---
# required metadata
title: Activate or deactivate Windows 365 disaster recovery plus
titleSuffix:
description: Learn how to activate or deactivate Windows 365 disaster recovery plus.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/07/2025
ms.topic: how-to
ms.service: windows-365
ms.subservice: windows-365-enterprise
ms.localizationpriority: high
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:

ms.reviewer: docoombs
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure; get-started
ms.collection:
- M365-identity-device-management
- tier2
---

# Activate or deactivate disaster recovery plus in Windows 365

During an outage or for testing, you can activate or deactivate Windows 365 disaster recovery plus to move users to their temporary Cloud PCs and back. Disaster recovery plus is designed for use during a large-scale event, with the temporary Cloud PCs activated and deactivated from the Intune admin center.

Using bulk actions, you can activate/deactivate cross region disaster recovery for individual devices or devices for all users in a group.

Activating disaster recovery plus moves users to a new temporary Cloud PC in a temporary region. Users can’t access the new Cloud PCs until the move is complete. Until the disaster recovery plus is deactivated, users work with the temporary Cloud PC in alternate region.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) > **Devices** > **All devices** > **User settings**> **Bulk device actions**.
2. On the **Basics** page, select the following options:
    - **OS**:  **Windows**
    - **Device type**: **Cloud PCs**
    - **Device action**: **Optional disaster recovery**
    - **Optional disaster recovery**: **Activate disaster recovery plus** or **Deactivate disaster recovery plus**
3. Select **Next**.
4. On the **Devices** page, select at least one device > **Next**.
5. On the **Review + create** page, select **Create**.

<!-- ########################## -->
## Next steps

Learn how to [set up](disaster-recovery-plus-set-up.md) disaster recovery plus.
