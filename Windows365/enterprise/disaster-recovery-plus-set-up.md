---
# required metadata
title: Set up disaster recovery plus in Windows 365
titleSuffix:
description: Learn how to set up disaster recovery plus in Windows 365.
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

# Set up disaster recovery plus

To configure [disaster recovery plus](disaster-recovery-plus.md), use the following steps. For more information about user settings, see [User settings](assign-users-as-local-admin.md).

> [!IMPORTANT]  
> When using disaster recovery plus, it's critical to configure and test the entire cross region flow as part of your repeating [business continuity and disaster recovery planning](../business-continuity-disaster-recovery.md). Before releasing widely across your whole environment, you should activate and deactivate multiple test devices to make sure that it's working as expected. You should also periodically check that your environment is healthy and configured correctly by using the [**Cloud PC optional business continuity and disaster recovery status** report](cloud-pc-optional-business-continuity-disaster-recovery-status-report.md).

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) > **Devices** > **Windows 365**(under **Device Onboarding**)> **User Settings**.
2. Select **Create** (alternately, you can make the following changes to an existing user setting).
3. On the **Settings** page, type a name in the **Name** box.
4. Set the values under **Point-in-time restore service** per your requirements. These values also apply to disaster recovery plus.
5. Select **Optional Business Continuity and Disaster Recovery Settings**.
6. For **Enable additional DR for this User Setting**, select **Disaster Recovery Plus**.
7. Select the **Network type** for your environment. If you select Azure network connection (ANC), you must configure a network and Azure Network Configuration in your alternate region to support your Cloud PCs when they are restored in that region.

    - For **Enable cross region disaster recovery**, select *Yes*.
    - For **Network type**, select an option:
      - **Microsoft-hosted network**: Select the **Geography** and **Region** where your Cloud PC backups are created for cross region disaster recovery.
      - **Azure network connection** (ANC): Your selected ANC determines where the Cloud PC backups are created for cross region disaster recovery. You must configure your ANC for your backup region to support the restored Cloud PCs.

    When configuring a backup location, consider things like data sovereignty and geographic distance between the user and the Cloud PC backup location. The greater the distance between your backup Cloud PC and your user’s connect location increases network latency and impacts performance. Full copies of your Cloud PCs are kept in the backup location, including all data stored on the Cloud PC disk.

6. Select **Next**.
7. On the **Assignments** page, add the groups containing users that you want this user setting applied to. All Cloud PCs associated with a user will share the same cross region disaster recovery settings.

8. On the **Review + create** page, select **Create**.

After you finish this configuration, the first backup of the Cloud PC may take several days. To see the current state of backups, check the [Cross region disaster recovery report](cross-region-disaster-recovery-report.md). After the first backup, the recovery point objective (RPO) will be the same as for point-in-time restore plus a few minutes to replicate across regions.

<!-- ########################## -->
## Next steps

Learn how to [activate/deactivate](cross-region-disaster-recovery-activate.md), and [monitor](cross-region-disaster-recovery-report.md) cross region disaster recovery.
