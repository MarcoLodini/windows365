---
# required metadata

title: In development - Windows 365 Enterprise
description: Windows 365 Enterprise features in development
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/19/2025
ms.topic: whats-new
ms.service: windows-365

# optional metadata

#audience:

ms.reviewer: traceyadams
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: references_regions
ms.collection:
- M365-identity-device-management
- tier2
ms.subservice: windows-365-enterprise
---

# In development for Windows 365 Enterprise

To help in your readiness and planning, this page lists Windows 365 updates and features that are in development but not yet released. In addition to the information on this page:

- If we anticipate that you need to take action before a change, we publish a complementary post in Office message center.
- When a feature enters production, the feature description moves from this page to [What's new](whats-new.md).
- This page and the [What's new](whats-new.md) page are updated periodically. Check back for more updates.
- Similar features might be announced at different times for Windows 365 Business.

> [!NOTE]
> This page reflects our current expectations about Windows 365 capabilities in an upcoming release. Dates and individual features might change. This page doesn't describe all features in development.

**This article was last updated on the date listed under the title above.**

<!-- Common categories:  
## App management
## Device configuration
## Device provisioning
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security
## End-user experience

-->

<!-- ***********************************************-->
## Device management

### Windows 365 disaster recovery options<!--55482055-->

In a future update, admins will have two options for disaster recovery: the existing cross region disaster recovery and the new disaster recovery plus. The latter allocates a second Cloud PC at the time of configuration which improves restore time objective (RTO). As the recovery Cloud PC already exists, there isn't a capacity risk at the time of failure.

### Resize Windows 365 Frontline Cloud PCs in designated mode<!--54353038-->

Admins will be able to resize Windows 365 Frontline Cloud PCs in designated mode.

<!-- ***********************************************-->
## Device security

### Windows 365 Government support for Microsoft Purview Customer Key<!--48232935-->

Windows 365 Government will support encrypting Cloud PCs by setting up Microsoft Purview Customer Key. For more information, see [Service encryption with Microsoft Purview Customer Key](/purview/customer-key-overview).

<!--***********************************************-->
<!-- ## End user experience -->

<!-- ***********************************************-->
## Miscellaneous

### More regions adding to global TURN relay support<!--56400921-->

TURN relay support will be improved by expanding from 14 to over 40 regions globally. This expansion will reduce latency and improve connection reliability by serving users from more diverse locations. The dedicated IP range for Windows 365 traffic, separate from the ACS TURN relay, will optimize and isolate traffic for AVD and Windows 365. This will let customers bypass certain network restrictions and enhance the quality and speed of Windows 365 traffic.

<!-- ***********************************************-->
## Monitor and troubleshoot

### End user manual connectivity check<!--37679345 -->

End users will be able to manually run connectivity checks on their Cloud PCs from [windows365.microsoft.com](https://windows365.microsoft.com).

<!-- ***********************************************-->
## Provisioning

### Credential Guard and HVCI enabled by default<!--554824970-->

In a future update, newly provisioned and reprovisioned Cloud PCs will have Virtualization-based Security (VBS), Hypervisor-protected Code Integrity (HVCI), and Credential Guard enabled by default.

<!-- ***********************************************-->
<!--## Security-->

<!-- ***********************************************-->
## Windows 365 Boot

### Return to local desktop<!--56381979-->

When in Windows 365 Boot mode (Windows 11 only), users will be able to switch back to their physical device desktop from either:

- CTRL-ALT-DEL screen
- Cloud PC error screens
Administrators will be able to configure and customize this feature within the Guided Scenario for Boot.

<!-- ***********************************************-->
## Windows 365 Frontline

### Resize Windows 365 Frontline Cloud PCs in dedicated mode<!--54353038-->

Admins will be able to resize Windows 365 Frontline Cloud PCs in dedicated mode.

## Next steps

For details about recent developments, see [What's new in Windows 365](whats-new.md).
