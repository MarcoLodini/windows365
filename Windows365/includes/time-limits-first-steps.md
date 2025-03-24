---
title: include file
description: include file
author: ErikjeMS  
ms.service: windows-365
ms.topic: include
ms.date: 04/02/2025
ms.author: erikje
ms.custom: include file
---

1. Sign in to [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** > **Configuration** (under **Manage devices**) > **Create** > **New policy**.
2. Under **Create a profile**, select the following options:

    - **Platform**: Windows 10 and later
    - **Profile type**: Settings catalog

3. Select **Create**.
4. On the **Basics** page, provide a name and optional description > **Next**.
5. On the **Configuration settings** page, select **Add settings**.
6. Under **Settings picker**, search for "session time limits".
7. Under **Browse by category**, select **Administrative Templates\Windows Components\Remote Desktop Services\Remote Desktop Session Host\Session Time Limits**.