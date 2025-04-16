---
# required metadata
title: Microsoft and customer responsibilities for Windows 365
titleSuffix:
description: Learn the responsibilities of Microsoft and customers for Windows 365.
keywords:
author: ErikjeMS  
ms.author: erikje
manager: dougeby
ms.date: 04/16/2025
ms.topic: overview
ms.service: windows-365
ms.subservice: windows-365-enterprise
ms.localizationpriority: high
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:

ms.reviewer: shupadhyaya
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure; get-started
ms.collection:
- M365-identity-device-management
- tier2
---

# Microsoft and customer roles and responsibilities for Windows 365

Windows 365 follows a shared responsibility model like the [rest of the online services in the Microsoft Cloud](/compliance/assurance/assurance-risk-assessment-guide). The responsibilities for managing Windows 365 are clearly divided between Microsoft and the customer:

- Microsoft is responsible for the security and compliance of the cloud infrastructure.
- Customers  are responsible for managing and configuring security and compliance in the cloud according to their specific needs and risk tolerance.

For more information, see [Windows 365 service description service responsibility section](/office365/servicedescriptions/windows-365-service-description/windows-365-service-description?branch=main#service-responsibility).

If a service incident occurs, Microsoft might temporarily adjust infrastructure, networking, or other managed components to restore or maintain the stability and availability of the Windows 365 service. These adjustments ensure reliable operation and uninterrupted user access.

This document applies only to Windows 365 and doesn't apply to any other Microsoft online services or products, including the Windows operating system. This document doesn't supersede any product terms or the service level agreement (SLA) for Windows 365. For more information, see the [Windows 365 Service Description](/office365/servicedescriptions/windows-365-service-description/windows-365-service-description) and [SLA](https://www.microsoft.com/licensing/docs/view/Service-Level-Agreements-SLA-for-Online-Services).


## Microsoft responsibilities

**Change management**:  Microsoft manages all service infrastructure updates and changes in accordance with SOC 2 and ISO 27001 standards.

**Gallery image**: Production and publication of gallery images on a monthly basis.

**Intune enrollment**: Microsoft makes sure that Cloud PCs are automatically enrolled in Microsoft Intune. An exception to this automatic enrollment is when the customer uses Windows 365 Business and doesn't choose automatic enrollment or lacks the required licensing.

**Network connectivity**:

[!INCLUDE [Network connectivity roles for Microsoft](./includes/roles-network-connectivity-microsoft.md)]

**Security and compliance**: Microsoft manages risks related to fraud, abuse, and malicious activity as explained in the [Product Use Rights](/legal/windows-365/windows-365-app-license-terms) and the [Microsoft Online Services Agreement](https://www.microsoft.com/servicesagreement/).

**Service critical components**: Microsoft deploys, manages, and maintains the critical components needed to reliably deliver Windows 365, as outlined in the Service Description and SLA. These components include: Service agents: RD-Agent, Azure Agent, CMD Agent.

**Service-level commitments**: Microsoft makes sure Windows 365 availability and performance as defined in the SLA.


## Customer responsibilities

**Change management**: Integrating and testing Microsoft’s service changes within the organization's IT environment.

**Licensing**: Assignment and managing Windows 365 licenses to end users.

**Network connectivity**:
[!INCLUDE [Network connectivity roles for customers](./includes/roles-network-connectivity-customer.md)]

**Ongoing configurations**: Managing configurations like time zone redirection, USB redirection, and location redirection.

**Operating system and application management**: Installing updates, configuring settings, and managing OS and application lifecycles running on their Cloud PCs. This responsibility excludes the service-critical components that are Microsoft responsibilities.

**Security and compliance**: Customers implementing endpoint security policies, antivirus protection, regulatory compliance measures, and monitoring security threats to the Cloud PC's operating system.

**User management and authentication**: Managing user accounts, access permissions, and identity security.

## Shared responsibilities

For shared responsibilities, such as network connectivity and security, customers must understand their role and take appropriate action when needed. This clear division promotes efficient operation and security of the Windows 365 environment.

Microsoft deploys some configurations and components during the initial provisioning of a Cloud PC. After deployment, customers are responsible for their ongoing management and configuration. Examples of such configurations and components include:

- Microsoft 365 Apps.
- Multimedia redirection plug-in.
- Windows operating system configurations, such as disabling port 3389, or enabling security features like Hypervisor-protected Code Integrity (HVCI) and Credential Guard through supported management tools.

**Network connectivity**:
[!INCLUDE [Network connectivity roles for Microsoft](./includes/roles-network-connectivity-microsoft.md)]

[!INCLUDE [Network connectivity roles for customers](./includes/roles-network-connectivity-customer.md)]

**Security and monitoring**: Microsoft secures the cloud infrastructure. Customers manage Windows client OS and application security running in the cloud.

**Support and troubleshooting**: Microsoft provides platform-level support. Customers handle OS-level issues, application troubleshooting, and user-related concerns.

<!-- ########################## -->
## Next steps

[Windows 365 Service Description](/office365/servicedescriptions/windows-365-service-description/windows-365-service-description) and [SLA](https://www.microsoft.com/licensing/docs/view/Service-Level-Agreements-SLA-for-Online-Services)
