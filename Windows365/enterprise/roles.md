---
# required metadata
title: Get help from App Assure for apps on Cloud PCs
titleSuffix:
description: Learn how to use App Assure to get help for apps on Cloud PCS.
keywords:
author: ErikjeMS  
ms.author: erikje
manager: dougeby
ms.date: 07/24/2024
ms.topic: overview
ms.service: windows-365
ms.subservice: windows-365-enterprise
ms.localizationpriority: high
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:

ms.reviewer: elwort
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure; get-started
ms.collection:
- M365-identity-device-management
- tier2
---

# Roles and responsibilities

| Area | Microsoft responsibilities | Shared responsibilities | Customer responsibilities |
| --- | --- | --- | --- |
| Service critical components | Microsoft deploys, manages, and maintains the critical components needed to reliably deliver Windows 365, as outlined in the Service Description and SLA. These components include: Service agents: RD Agent, Azure Agent, CMD Agent. |  |  |
| Network connectivity | For Microsoft-hosted networks, Microsoft manages network connectivity for Windows 365, including Azure Networking and on-site infrastructure configurations (firewall, proxy, and other settings). However, customers are responsible for any operating system-level networking configurations they implement, including third-party software that may impact network access such as VPNs, custom proxies, or traffic inspection tools. | For Azure Network Connection (ANC), customers are responsible for networking security and configuration under their control, including virtual network (vNet) settings, firewalls, and routing. Misconfigurations in these areas can impact connectivity to their Cloud PCs. <br> For Microsoft-hosted networks , Microsoft manages network security and RDP connectivity, ensuring a stable connection. <br> In both ANC and Microsoft-hosted networks, customers are responsible for any operating system-level networking configurations or network security controls they apply, including third-party agents such as VPNs, proxies, or traffic inspection tools that may affect network connectivity. | In ANC, customers manage security, network configurations, VPNs, proxies, and any other network components under their control. They must ensure proper configuration of their virtual network (vNet), as any misconfigurations can impact connectivity to their Cloud PCs. <br> In Microsoft-hosted networks, Microsoft manages the core network infrastructure, but customers remain responsible for any operating system-level networking configurations they apply. This includes third-party software that may impact network access, such as VPNs, proxies, and traffic inspection tools. |
| Security and monitoring/compliance | Microsoft manages risks related to fraud, abuse, and malicious activity per the Product Use Rights and the Microsoft Online Services Agreement. | Microsoft secures the cloud infrastructure, while customers manage Windows client OS and application security running in the cloud. | Implementing endpoint security policies, antivirus protection, regulatory compliance measures, and monitoring security threats to the Cloud PC's operating system. |
| Gallery image | Production and publication of gallery images on a monthly basis. |  |  |
| Intune enrollment | Microsoft makes sure that Cloud PCs are automatically enrolled in Microsoft Intune unless the customer is using Windows 365 Business and hasn’t chosen automatic enrollment or lacks the required licensing. |  |  |
| Service-level commitments | Microsoft makes sure Windows 365 availability and performance as defined in the SLA. |  |  |
| Change management | Microsoft manages all service infrastructure updates and changes in accordance with SOC 2 and ISO 27001 standards. |  | Integrating and testing Microsoft’s service changes within the organization's IT environment. |
| Support and troubleshooting |  | Microsoft provides platform-level support, while customers handle OS-level issues, application troubleshooting, and user-related concerns. |  |
| OS and application management |  |  | Installing updates, configuring settings, and managing OS and application lifecycles running on their Cloud PCs, excluding the service-critical components mentioned above in the Microsoft responsibilities section. |
| User management and authentication |  |  | Managing user accounts, access permissions, and identity security. |
| Licensing |  |  | Assignment and managing Windows 365 licenses to end users. |
| Ongoing configurations |  |  | Managing configurations like time zone redirection, USB redirection, and location redirection. |
|  |  |  |  |
| --- | --- | --- | --- |



<!-- ########################## -->
## Next steps
