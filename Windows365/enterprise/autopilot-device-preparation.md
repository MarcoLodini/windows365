---
# required metadata
title: Use Autopilot device preparation with Cloud PCs
titleSuffix:
description: Learn how to use Autopilot device preparation with Cloud PCs.
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

ms.reviewer: ericor
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure; get-started
ms.collection:
- M365-identity-device-management
- tier2
---

# Use policy-driven Autopilot device preparation with Windows 365 Frontline Cloud PCs in shared mode

When provisioning Cloud PCs, you can optionally link [Autopilot device preparation](/autopilot/device-preparation/overview) to help make sure Windows 365 Frontline Cloud PCs in shared mode are provisioned with important Intune apps and scripts.



## Link policy-driven device preparation policies to Cloud PCs

1. Meet the [Windows Autopilot device preparation requirements](/autopilot/device-preparation/requirements).
2. When [creating a new](create-provisioning-policy.md) or [editing an existing](edit-provisioning-policy.md) Windows 365 provisioning policy also complete the following steps:

    1. On the **Configuration** tab, for **Autopilot device preparation policy**, select a policy.
    2. For **Minutes allowed before device preparation fails**, type a value for that allows adequate time to install the apps and scripts defined in your policy. If the apps and scripts aren't finished installing by this time, the device preparation fails (but the provisioning continues).
    3. Optionally, you can select **Prevent users from connection to Cloud PC upon installation failure or time-out** option to force the provisioning result to **Failed** if there's a time-out or failure. If selected, Cloud PCs that fail to complete device preparation policy installation are marked as **Failed**. In this case, users can't connect to them. If not selected, Cloud PCs are marked as **Provisioned with warnings** and users can connect to their Cloud PCs.

3. Complete the remaining steps to [create a new](create-provisioning-policy.md) or [edit an existing](edit-provisioning-policy.md) Windows 365 provisioning policy

Windows 365 completes the provisioning process after:

- The apps and scripts are successfully installed.
- The time-out value expires.

## Monitor status of device preparation on Cloud PCs

To see the status of device preparation for Cloud PC provisioning, go to **Devices** > **Enrollment** > **Monitor** > **Windows Autopilot device preparation deployment status**.

<!-- ########################## -->
## Next steps

[Learn more about Windows Autopilot device preparation](/autopilot/device-preparation/overview).
