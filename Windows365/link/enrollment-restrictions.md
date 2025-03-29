---
# required metadata
title: Configure enrollment restrictions for Windows 365 Link devices
titleSuffix:
description: Learn how to configure enrollment restrictions for Windows 365 Link devices.
keywords:
author: ErikjeMS  
ms.author: erikje
manager: dougeby
ms.date: 11/19/2024
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

# Configure enrollment restrictions

While [setting up your organization's environment to support Windows 365 Link](deployment-overview.md), you should make sure that your environment's enrollment restrictions don't block Windows 365 Link devices from enrolling in Intune.

The [first time a user signs in](setup.md) during the Out of Box Experience (OOBE), Windows 365 Link devices use [Automatic MDM enrollment](intune-automatic-enrollment.md) with [Microsoft Entra join during Windows setup](join-microsoft-entra.md).  Initially, the device is considered Unknown at the time of enrollment, but after the join, the device is set to Corporate-owned.

Any [device platform restriction](enrollment-restrictions.md) that blocks personally-owned Windows devices also blocks Unknown devices. This kind of restriction also blocks Windows 365 Link devices from completing Intune enrollment.

To ensure Windows 365 Link devices can be enrolled in Intune, use any of the following methods:

- [Use  corporate identifiers to mark Windows 365 Link devices as corporate-owned](/mem/intune/enrollment/corporate-identifiers-add#add-windows-corporate-identifiers).
- [Use an operating system SKU filter to let Windows 365 Link devices enroll](#use-an-operating-system-sku-filter-to-allow-windows-365-link-devices-to-enroll-in-intune).
- [Use a Device Enrollment Manager (DEM) to bypass all restrictions](/mem/intune/enrollment/device-enrollment-manager-enroll).

## Use corporate identifiers to mark Windows 365 Link devices as corporate-owned

Adding corporate identifiers makes sure that devices are marked as corporate-owned as soon as they are enrolled. Platform restrictions that block unknown or personally-owned devices don’t block devices that match a corporate identifier.

To add Windows corporate identifiers for Windows 365 Link devices, follow these steps:

1. Create a comma-separated list of the manufacturer, model, and serial number for each device as shown in the following exampl:

    `Microsoft Corporation,Windows 365 Link,01234567890123`<br>
    `Microsoft Corporation,Windows 365 Link,02234567890123`

    Serial numbers for Windows 365 Link devices can be found on the bottom of the device and on the original packaging.

2. Save the list as a CSV file.
3. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) > **Devices** > **Enrollment** > **Corporate device identifiers** > **Add** > **Upload CSV file**.
4. Select the identifier type: **Manufacturer, model, and serial number (Windows only)**.
5. Under **Import identifiers**, find and select the CSV file.
6. Wait while Intune validates the CSV file. When the total device identifiers count appears onscreen, validation is complete.
8. Select **Add**, and then look for the success notification at the top of the admin center to confirm that the file is imported.

Corporate Identifiers can also be added by using Graph API with the importDeviceIdentityList action.

To learn more about corporate identifiers, including the type of ownership given to devices when they enroll with or without corporate identifiers, see [Add corporate identifiers to Intune](/intune/intune-service/enrollment/corporate-identifiers-add).

## Use an operating system SKU filter to allow Windows 365 Link devices to enroll in Intune

If there's a policy that blocks personally owned Windows devices from enrolling in Intune it also blocks Windows 365 Link devices. Instead of using Corporate Identifiers or a DEM, you can create another policy, with higher priority, to allow Windows 365 Link devices to enroll in Intune while still blocking unknown or personally-owned Windows devices.

Follow these steps to create a policy to allow users to enroll Windows 365 Link devices in Intune:

1. [Create an Intune filter for Windows 365 Link devices](create-intune-filter.md).
2. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) > **Devices** > **Enrollment** > **Windows** > **Device platform restriction** > **Windows restrictions**.
3. Under **Windows restrictions**, select **Create restriction**.
4. On the **Basics** page, type a **Name** (like *Allow enrollment of Windows 365 Link devices*) and an optional **Description** > **Next**.
5. On the **Platform settings** page, set the following options:
    - **MDM**: *Allow*
    - **Personally owned devices**: *Allow*
6. Select **Next**.
7. On **Scope tags** page, select **Next**.
8. On **Assignments** page, select **Add all users** > **Edit filter**.
9. On the **Filters** pane, select **Include filtered devices in assignment** > **Windows 365 Link** > **Select**.
10. Select **Next**.
11. On the **Review + create** page, select **Create**.
12. On the **Enrollment restrictions** > **Windows restrictions** page, make sure the new policy is above any block policy in priority order.

For more information about Intune platform enrollment restrictions, see [Create device platform restrictions](/mem/intune/enrollment/create-device-platform-restrictions).

## Use a Device Enrollment Manager to bypass enrollment restrictions

A DEM can enroll devices that are normally blocked by a platform restriction policy.  A DEM is also not blocked by Intune device limit restrictions. Using a DEM is recommended for scenarios where the Windows 365 Link device doesn’t have a dedicated owner.

After you designated an account as a DEM, the account can be used to enroll up to 1,000 devices. However, there is a separate limit on the number of devices any user is allowed to join to Entra ID.  

Follow these steps to designate an account as a DEM in Intune:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) > **Devices** > **Enrollment** > **Device enrollment managers** > **Add**.
2. In the **User name** field, enter the user principal name of the user you're adding.
3. Select **Add**. The new device enrollment manager is added to the list of DEM users.

For more information about DEMs, see [Add device enrollment managers]( /intune/intune-service/enrollment/device-enrollment-manager-enroll).



<!-- ########################## -->
## Next steps

[Suppress single sign-on consent prompt](single-sign-on-suppress.md).
