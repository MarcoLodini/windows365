---
# required metadata
title: Set session time limits for Windows 365 Frontline Cloud PCs
titleSuffix:
description: Learn how to set session time limits for Windows 365 Frontline Cloud PCs
keywords:
author: ErikjeMS  
ms.author: erikje
manager: dougeby
ms.date: 04/02/2025
ms.topic: how-to
ms.service: windows-365
ms.subservice: windows-365-enterprise
ms.localizationpriority: high
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:

ms.reviewer: gkomatsu
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure; get-started
ms.collection:
- M365-identity-device-management
- tier2
---

# Set session time limits for Windows 365 Frontline Cloud PCs

Session time limits define how long users are inactive in your organization before they're signed out of their Windows 365 Frontline Cloud PC session. There are two kinds of time limits:

- Time limits for active but idle Remote Desktop Services session.
- Time limits for disconnected sessions.

Time limits help protect sensitive company data and add another layer of security for end users who work on shared devices.

## Windows 365 Frontline Cloud PCs in dedicated mode

Windows 365 Frontline Cloud PCs in dedicated mode keep the user session active until:

- The Cloud PC is idle for 30 minutes (default value). Two minutes before the idle time limit, the user is notified with a dialog box.
- The user signs off from the Cloud PC through the start menu.
- The browser or Windows App is closed (causing the Cloud PC to disconnect).

Windows 365 Frontline Cloud PCs in dedicated mode remain powered on for two hours after the user session becomes inactive. During this inactive time, session concurrency isn't consumed.

## Windows 365 Frontline Cloud PCs in shared mode

Windows 365 Frontline Cloud PCs in shared mode keep the user session active until:

- The Cloud PC is idle for 15 minutes (default value).
- The user signs off from the Cloud PC through the start menu.
- The user session remains disconnected for over 30 minutes (default value).  

If a user forgets to disconnect or sign out, it might block others from connecting to Frontline Cloud PCs because the max active session limit has been reached. To avoid this problem, you can create a configuration profile to enforce idle session time limits and disconnect time limits on all your Frontline Cloud PCs.

## Change idle session time limits

Idle session time limits define how long until a user is automatically disconnected from a Windows 365 Frontline Cloud PC.

[!INCLUDE [Time limits first steps](../includes/time-limits-first-steps.md)]

1. Select the box for **Set time limit for active but idle Remote Desktop Services session**.
1. Under **Create profile**, expand **Administrative Templates** > enable **Set time limit for active but idle Remote Desktop Services sessions**.
1. For **Idle session limit: (Device)**, select a time limit that meets your company's compliance requirements. When a Frontline Cloud PC is idle for this period of time, the Cloud PC is automatically disconnected.

[!INCLUDE [Time limits last steps](../includes/time-limits-last-steps.md)]

## Change disconnect session time limits

Disconnect session time limits are the time until the user is automatically signed-out from the Frontline Cloud PC.

[!INCLUDE [Time limits first steps](../includes/time-limits-first-steps.md)]
1. Select the box for **Set time limit for disconnected sessions**.
1. Under **Create profile**, expand **Administrative Templates** > enable **Set time limit for disconnected sessions**.
1. For **End a disconnected session (Device)**, select a time limit that meets your company's compliance requirements. When a Frontline Cloud PC is disconnected for this period of time, the user is automatically signed out from the Cloud PC.
[!INCLUDE [Time limits last steps](../includes/time-limits-last-steps.md)]

<!-- ########################## -->
## Next steps

[Manage your Cloud PCs](device-management-overview.md).
