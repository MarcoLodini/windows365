---
# required metadata
title: Wipe or Rest Windows 365 Link device
titleSuffix:
description: Learn about options to return a Windows 365 Link device to factory defaults.
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

ms.reviewer: ketrem
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure; get-started; intro-hub-or-landing
ms.collection:
- M365-identity-device-management
- tier2
---

# Wipe or reset Windows 365 Link device

You can return  Windows 365 Link devices to their factory default state. This return to factory settings can be useful:

- when experiencing performance issues or software problems
- to repurpose the device.

There are three ways to return a Windows 365 Link device to its factory default state:

- Intune Wipe remote device action.
- Company Portal Reset.
- Windows Recovery Environment reset.

After completing one of these methods to restore the Windows 365 Link device to its original factory default state, the next time a user turns it on they’ll be prompted through the [Setup and sign-in process](setup.md) as a first-time user of the device.

## Intune Wipe remote device action

You can use the Intune Wipe device action to restore a Windows 365 Link device to its factory default settings. For more information, see [Wipe](/mem/intune-service/remote-actions/devices-wipe#wipe).

## Company Portal Reset

You can use the Company Portal app for Windows to reset a Windows 365 Link device back to factory settings.

For more information, see [Reset device in Company Portal app for Windows]( /mem/intune-service/user-help/reset-device-company-portal-windows).

## Windows Recovery Environment Reset

Windows Recovery Environment (WinRE) can, among other things, reset a Windows 365 Link device back to factory defaults.

For more information, see [Windows Recovery Environment (Windows RE)](/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference?view=windows-11).

For Windows 365 Link devices, WinRE starts automatically after detecting the following issues:

- Two consecutive failed attempts to start Windows.
- Two consecutive unexpected shutdowns that occur within two minutes of boot completion.
- Two consecutive system reboots within two minutes of boot completion.
- A Secure Boot error (except for issues related to Bootmgr.efi).

A BitLocker recovery key for the device is required To start a device reset from WinRE. For instructions on how to get the key, see [Self-recovery in Microsoft Entra ID](/windows/security/operating-system-security/data-protection/bitlocker/recovery-process#self-recovery-in-microsoft-entra-id). 

<!-- ########################## -->
## Next steps

[Set up your Windows 365 Link and sign in](setup.md)
