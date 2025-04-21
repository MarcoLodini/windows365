---
# required metadata
title: Windows 365 disaster recovery plus
titleSuffix:
description: Learn about Windows 365 disaster recovery plus.
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/07/2025
ms.topic: overview
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

# Windows 365 disaster recovery plus

Windows 365 disaster recovery plus is an optional service for Windows 365 Enterprise that helps improve disaster recovery and data resilience for Cloud PCs. Disaster recovery plus:

- Creates three copies of the Cloud PC OS disk to a different geography/region.
- Allocates and reserves capacity for a Cloud PC in the alternate region.

If there's an Azure regional level event that restricts access to Cloud PCs in the primary region, the disk copies can be used to restore the device to the allocated Cloud PC in the alternate region.

When you configure Windows 365 disaster recovery plus for a user, Windows 365 makes a copy of the OS disk for all of the user’s Cloud PCs, to the alternate geography/region you specify. The initial full disk copy may take up to three days, but subsequent incremental copies take only minutes.

## Compared to point-in-time restore and cross region disaster recovery

To successfully restore a Cloud PC during an outage, [point-in-time restore](restore-overview.md) to an alternate zone and [cross region disaster recovery](cross-region-disaster-recovery.md)  depend on the target region/zone capacity.

Windows 365 disaster recovery plus allocates resources when configured, proactively reserving the resources. This proactive allocation greatly increases the likelihood that the restore succeeds.

If a point-in-time restore fails due to capacity constraints, Windows 365 Disaster Recovery Plus provides a secondary opportunity to restore the Cloud PC to the reserved capacity of the alternate region.

## Restore point objective and restore time objective

If there's an outage, the service has the following target objectives for disaster recovery plus:

- Restore point objective (RPO) of < 61 minutes.
- Restore time objective (RTO) of < 31 minutes.

Devices are restored as quickly as possible.

## Temporary Cloud PC

When activated, disaster recovery plus temporarily creates a copy of the users’ Clouds PCs in an alternate region. It uses the latest restore point for each Cloud PC, and includes all installed applications, user settings, and data.

The user is shown a warning message when using the temporary Windows 365 Disaster Recovery Plus device.

When you deactivate disaster recovery plus after the outage event, the temporary Cloud PC is deleted. No applications, settings, data, or other information is preserved from the temporary Cloud PC. Nothing that the user saves to the temporary Cloud PC is replicated back to the primary device.

<!-- ########################## -->
## Next steps

[Set up disaster recovery plus](disaster-recovery-plus-set-up.md).
