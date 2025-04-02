---
# required metadata
title: Set Windows 365 Link devices to auto detect current time zone
titleSuffix:
description: Learn how to set Windows 365 Link devices to auto detect current time zone
keywords:
author: ErikjeMS  
ms.author: erikje
manager: dougeby
ms.date: 04/02/2025
ms.topic: how-to
ms.service: windows-365-link
ms.subservice:
ms.localizationpriority: high
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:

ms.reviewer: sajelaci
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure; get-started; intro-hub-or-landing
ms.collection:
- M365-identity-device-management
- tier2
---

# Set Windows 365 Link devices to auto detect current time zone

You can enforce the local time zone on Windows 365 Link devices by following these steps: 

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) > **Devices** > **Configuration** (under **Manage devices**) > **Create** > **New Policy**.
2. Under **Create a profile**, select the following options:
    - **Platform**: **Windows 10 and later**
    - **Profile Type**: **Settings catalog**
3. Select **Create**.
4. Enter a **Name** for the policy, like "Windows 365 Link Time Zone Detection" and a useful **Description**.
5. Select **Next**.
6. On the **Configuration settings** page, select **Add settings**.
7. Search for **Privacy** and select that category.
8. Select **Let apps Access Location** and  **Let Apps Access Location Force Allow These Apps**.
9. Select **Next**.
10. On the **Scope tags** page, select any desired scope tags to apply, then select **Next**.
11. On the **Assignments** page, target Windows 365 Link devices per your preferred method. For example, you can use **Add all devices** with an **Include** filter using a Windows 365 Link device filter. This filter targets the policy at all Windows 365 Link devices.
12. Select **Next**.
13. On the **Review + create** page, review the settings.
14. Select **Create** to deploy the profile.

<!-- ########################## -->
## Next steps

[Manage Windows 365 Link devices](device-management-overview.md).
