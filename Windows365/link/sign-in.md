---
# required metadata
title: Sign in to your Windows 365 Link
titleSuffix:
description: Learn how to sign in, sign our, and lock your Windows 365 Link
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

# Sign in to, sign out, or lock your Windows 365 Link

When you want to use the Windows 365 Link, complete the following steps to sign in:

1. Power on the Windows 365 Link.
2. On the **Sign in** screen, provide your sign in credentials. The device automatically presents you with the sign-in process configured by your organization (FIDO2 security key, Passkey (FIDO2), Microsoft Authenticator app, and so on).
3. Authenticate your account as requested.
4. You're connected to your Cloud PC.

## Sign out

To sign out of your Windows 365 Link:

1. Press control-alt-delete.
2. Select **Sign out**.

Signing out disconnects the current signed in user from their Cloud PC and brings Windows 365 Link back to the sign-in screen.

## Lock or disconnect your Windows 365 Link

Lock the device using any of these methods:

- Press the **Windows key + L** on your keyboard.
- Select **Start** > **Power** > **Lock**.
- In your Cloud PC, select start > **Power** > **Disconnect**.
- In your Cloud PC, select start > **Power** > **Lock**.\*

\* This method lock the remote session on the Cloud PC. Single sign-on connections are also disconnected (but admins can configure policies to behave differently).

After the user locks the device, the user is redirected back to the **Sign in** screen. The previous user's Cloud PC connection persists for 15 minutes by default, allowing for quick reconnection if the user had to temporarily step away, returns to the device, and signs in again.

If Windows 365 Link is locked, the current signed in user’s connection to their Cloud PC is maintained until Cloud PC’s idle time-out expires. Within this time window, if the user unlocks Windows 365 Link by completing the authentication experience again, they're taken directly on their Cloud PC without the need for re-establishing the connection.

## Data

Your data and account information aren't stored on the Windows 365 Link. If someone else signs into their account on the Windows 365 Link, the previous user's Cloud PC connection is automatically disconnected and the new user has no access to the previous user's data.

## Multiple Cloud PCs

If you have more than one Cloud PC, you can select a default Cloud PC to use each time you sign in. To set this default:

1. Navigate to [https://windows365.microsoft.com](https://windows365.microsoft.com).
2. In the card for the Cloud PC you want to set as default, select the ellipses (...) > **Settings**.
3. In the **Integrated experiences** tab, under **Boot to this Cloud PC**, select **Connect while signed into device**.
4. Select **Update**.

<!-- ########################## -->
## Next steps

[Use Quick Settings to view and manage monitors, languages, network connections, and more](quick-settings.md).

[Use the Control-Alt-Delete menu manage tasks, connections, sign-out, or lock your Windows 365 Link.](control-alt-delete.md)
