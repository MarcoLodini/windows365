---
# required metadata
title: Manage Windows 365 Link devices with Microsoft Intune
titleSuffix:
description: Learn how to manage Windows 365 Link devices with Microsoft Intune
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

# Device management overview for Windows 365 Link

You manage Windows 365 Link devices in Intune, similar to managing other Windows endpoints. However, there are fewer configuration decisions and management actions needed because of the smaller Windows CPC OS used by the device.

This article explains some of the helpful features and different features that apply when you’re managing Windows 365 Link devices with Intune.

For more information about managing Cloud PCs, see [Device management overview for Cloud PCs](../enterprise/device-management-overview.md).

## Compliance settings

The only [compliance settings](/intune/intune-service/protect/compliance-policy-create-windows) that apply to Windows 365 Link devices is [Device health](/intune/intune-service/protect/compliance-policy-create-windows?WT.mc_id=Portal-Microsoft_Intune_DeviceSettings#device-health). This compliance setting includes BitLocker, Secure Boot, and code integrity which are enabled by default (and can't be turned off) on Windows 365 Link.

For more information on compliance policies in general, see [Use compliance policies to set rules for devices you manage with Intune](/intune/intune-service/protect/device-compliance-get-started).

## Configuration service providers

For information on which configuration service provider (CSP) policies apply to Windows 365 Link, see [Supported configuration service provider policies for Windows 365 Link](configuration-service-provider-support.md).

## Device filters

[Intune device filters](/mem/intune-service/fundamentals/filters) can be created to identify Windows 365 Link devices based on the Windows CPC operating system.

## Intune endpoint security

Most of Intune’s endpoint security features don’t apply to Windows 365 Link. Windows 365 Link’s OS includes the [Microsoft for Defender endpoint detection and response](/defender-endpoint/overview-endpoint-detection-response) sensor. You can [onboard your Windows 365 Link devices to Defender for Endpoint](/defender-endpoint/configure-endpoints-mdm).

## Remote device actions

When Windows 365 Link is in sleep mode, it’s also in disconnected standby mode. While in this mode, the device doesn’t check in with Intune nor does it respond to [remote device actions](/intune/intune-service/remote-actions/device-management).

If remote device actions are taking longer than expected, the device might be in sleep mode. In this case, awaken the device by taking any of the following actions:

- Press the power button.
- Move the mouse.
- Press several keys on the keyboard.

## Intune features that don't apply to Windows 365 Link

There are several features that don’t apply to Windows 365 Link.

- **App management**: Windows 365 Link doesn’t run local applications so tasks and options for installing and managing apps don’t apply. If an app configuration policy targets Windows 365 Link devices, Intune continuously reports **Pending install** for the device. To avoid this situation, update such policies to exclude Windows 365 Link devices by using an Intune device filter.
- **Microsoft Defender Malware scanning**: Windows 365 Link doesn’t run the Windows Defender Malware component. Device actions like Quick scan, Full scan, and Update Windows Defender security intelligence don’t apply to Windows 365 Link. If you try to use one of these actions on Windows 365 Link devices, Intune doesn’t execute the action and displays the message **Initiating (action) failed**.
- **Device scripts and remediation**: Windows 365 Link’s strict code integrity policy only allows software to execute when needed for the solution. Remediation script packages don’t run on Windows 365 Link and don’t show up in scripts and remediations device status reports.
- **Autopilot**: Windows 365 Link doesn’t support Autopilot or Autopilot device preparation, including:
  - Autopilot enrollment
  - Onboarding configurations
  - Autopilot specific device actions like Autopilot Reset.

<!-- ########################## -->
## Next steps

[Windows 365 Link update behavior and control](update-behavior-control.md).
