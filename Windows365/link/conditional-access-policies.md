---
# required metadata
title: Conditional Access policies for Windows 365 Link
titleSuffix:
description: Learn about Conditional Access policies for Windows 365 Link
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

# Conditional Access policies for Windows 365 Link

As part of [setting up your organization's environment to support Windows 365 Link](deployment-overview.md), you must make sure that your Conditional Access policies accommodate both the login through and connection from Windows Cloud PC devices. If Conditional Access is used to protect resources used to access Windows 365 Cloud PCs as described in [Set conditional access policies for Windows 365](/windows-365/enterprise/set-conditional-access-policies), another Conditional Access policy must also be used to protect the user action to register or join devices. Failure to create this second policy may cause Windows 365 Link authentication to fail.

To decide if you need a user action policy, follow these steps:

1. Check if any policies are triggered when connecting to Windows 365 resources.
2. Create a new user action policy with the same access controls.

## How Windows 365 Link authentication works

Windows 365 Cloud PC devices authenticate in two consecutive stages:

1. Interactive sign-in: When the user signs in on the Windows 365 Link sign in screen, it can trigger Conditional Access policies applied to Register or Join devices actions. Users can be shown messages or get challenged for stronger, multifactor authentication methods. This stage generates the token that is used in the second stage.
2. Non-interactive connections to Cloud PC resources using single sign-on: This stage can trigger Conditional Access policies on resources like **Windows 365**, **Windows Cloud Login**, and **All resources**. Users can't be prompted or challenged in this stage. If stronger authentication is needed, the connection is interrupted, and the user is shown an error that [an interactive window can't be shown](/troubleshoot/windows-365/connection-error-interactive-window-not-shown).

## Review existing policies

You can use the **What if** tool to determine if any Conditional Access policies are applied to relevant Windows 365 Resources during the non-interactive connection stage. This includes a policy that is applied to **All resources** (formerly **All cloud apps**).

1. Sign in to the [Microsoft Entra admin center](https://aad.portal.azure.com/) > **Protection** > **Conditional Access** > **Policies** > **What if**.
2. For **User or Workload identity** select a user to test with.
3. For Cloud apps, actions, or authentication context, select **Any cloud app**.
4. For **Select target type** leave **Cloud app** selected.
5. Select **Select apps** then select the following resources, if they're available:
    - **Windows 365** (app ID 0af06dc6-e4b5-4f28-818e-e78e62d137a5).
    - **Azure Virtual Desktop** (app ID 9cdead84-a844-4324-93f2-b2e6bb768d07).
    - **Microsoft Remote Desktop** (app ID a4a365df-50f1-4397-bc59-1a1564b8bb9c).
    - **Windows Cloud Login** (app ID 270efc09-cd0d-444b-a71f-39af4910ec45).
6. Select **What If**.

Review each of the **Policies that will apply** and determine the access controls used to grant access to those resources and session settings. Note these policies for use when creating the new user action policies in the next section.

## Create new Conditional Access policy for interactive sign-in stage

Using the information you gathered from the **What if** tool in the previous section, you can now create a new Conditional Access policy to require the same controls for the sign-in stage.

1. Sign in to the [Microsoft Entra admin center](https://aad.portal.azure.com/) > **Protection** > **Conditional Access** > **Policies** > **New policy**
2. Give your policy a name. Consider using a meaningful standard for policy names.
3. Under **Assignments** > **Users**, select **0 users and groups selected**.
4. Under **Include**, select **All users** or select a group of users who will sign-in through Windows 365 Link devices.
5. Under **Exclude**, select **Users and groups** > select your organization's emergency access or break-glass accounts.
6. Under **Target resources** > **User actions**, select **Register or join devices**.
7. Under **Access controls** > **Grant**, use the same controls found earlier using the **What If** tool.
8. Confirm your settings and set **Enable policy** to **Report-only**.
9. Select **Create**.
10. After confirming the settings using report-only mode, change the **Enable policy** toggle from **Report-only** to **On**.

While these steps are specifically for enabling interactive authentication on Windows 365 Link devices, the resulting user action policy is also applied when users Register or Join devices to Microsoft Entra ID.

> [!VIDEO e83133df-aeab-4563-92c5-eff455f656b0]

For more information about creating Conditional Access policies for device registration, including potential conflicts, see [Require multifactor authentication for device registration](/entra/identity/conditional-access/policy-all-users-device-registration#create-a-conditional-access-policy).

For more information about user actions with Conditional Access, see [User actions](/entra/identity/conditional-access/concept-conditional-access-cloud-apps#user-actions).

For more information about creating Conditional Access policies for resources used for Windows 365, see [Set Conditional Access policies](../enterprise/set-conditional-access-policies.md).

<!-- ########################## -->
## Next steps

[Suppress single sign-on consent prompt](requirements.md#windows-365-sso-requirements).
