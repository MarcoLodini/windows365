---
# required metadata
title: Windows 365 Link update behavior and control
titleSuffix:
description: Learn about update behavior and control for Windows 365 Link devices
keywords:
author: ErikjeMS  
ms.author: erikje
manager: dougeby
ms.date: 04/02/2025
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

# Windows 365 Link device update behavior and control

Windows 365 Link devices update automatically using the same Windows Update Services used by Windows 11. The Windows 365 Link device checks for updates periodically.

## Update behavior

When an update is available and detected by a device that is powered on, the device:

1. Silently downloads the update.
2. Installs the update during the next reboot, or at 3AM when the device is not in use.  

Driver and firmware updates occur separately from OS updates, and are also applied during a reboot.

If the device receives driver/firmware updates and OS updates at the same time, both updates occur over one reboot.

## Check for updates

You can check for updates manually from the device information pane in the [quick settings menu](quick-settings).

## Pause updates

You can pause updates using the:

[Policy configuration service provider (CSP)]( /windows/client-management/mdm/policy-configuration-service-provider) > [Update area]( /windows/client-management/mdm/policy-csp-update) > [AllowAutoUpdate node](/windows/client-management/mdm/policy-csp-update#allowautoupdate).

Allowed values for Windows 365 Link devices include:

| Value | Description |
| --- | --- |
| 0 – 3 | Unavailable. Do not use. |
| 4 | Turn on automatic updates. |
| 5 | Turn off automatic updates. |

For more information about these values, see [AllowAutoUpdate node](/windows/client-management/mdm/policy-csp-update#allowautoupdate).

<!-- ########################## -->
## Next steps

[See other quick settings options](quick-settings.md).