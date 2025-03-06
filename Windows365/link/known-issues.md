---
# required metadata
title: Known issues for Windows 365 Link
titleSuffix:
description: Learn about known issues for Windows 365 Link
keywords:
author: ErikjeMS  
ms.author: erikje
manager: dougeby
ms.date: 12/04/2024
ms.topic: overview
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

# Known issues: Windows 365 Link

The following items are known issues for Windows 365 Enterprise.

## Missing or renamed options in Cloud PC Display settings app for Windows 365 Link device <!--53427829-->

When connecting to a Cloud PC from a Windows 365 Link device, some options aren't available in the **System** > **Display** app. Instead, you can use **Open additional settings** to adjust arrangement and scale of up to two monitors attached.

## Locking the Cloud PC does not take the user back to the **Sign in** screen <!--56487937-->

This can happen if you lock the device by selecting **Start** > **Power** > **Lock** inside your connection. To remediate:

1. Perform one of the other sequences to [lock or disconnect your Windows 365 Link](sign-in.md##lock-or-disconnect-your-windows-365-link)
2. Follow the steps to [configure session lock behavior](/azure/virtual-desktop/configure-session-lock-behavior?tabs=intune) for single sign-on connections such that the **Disconnect remote session on lock for Microsoft identity platform authentication** policy is set to **Enabled**.
