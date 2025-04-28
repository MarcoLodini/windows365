---
title: include file
description: include file
author: ErikjeMS  
ms.service: windows-365
ms.topic: include
ms.date: 04/28/2025
ms.author: erikje
ms.custom: include file
---

## Requirements

### Role requirements

To resize a Cloud PC, the admin must have certain built-in Microsoft Entra roles.

- For a Cloud PC provisioned with a direct assigned license, at least one of the following roles
  - Intune Service Administrator
  - Intune Reader + Cloud PC Admin roles
  - Intune Reader + Windows 365 Administrator
- For a Cloud PC provisioned with a group-based license, at least one of the following roles
  - Intune Service Administrator
  - Intune Reader + Windows 365 Administrator
  - In addition to one of the previous three roles, a role with Microsoft Entra group read/write membership and licensing permissions, like the Windows 365 Admin role.

Alternatively, you can assign a custom role that includes the permissions of these built-in roles.

[!INCLUDE [Resize a Cloud PC IP requirements](../includes/resize-ip-address-requirements.md)]

[!INCLUDE [Resize a Cloud PC other requirements](../includes/resize-other-requirements.md)]
