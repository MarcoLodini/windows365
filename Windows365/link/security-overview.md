---
# required metadata
title: Windows 365 Link security
titleSuffix:
description: Learn about Windows 365 Link security
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

ms.reviewer: dawells
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure; get-started; intro-hub-or-landing
ms.collection:
- M365-identity-device-management
- tier2
---

# Windows 365 Link security

Built on a secure-by-design foundation with default patterns, Windows 365 Link sets a high-security posture for the endpoint. The following features support this security posture:

- Security features that can’t be disabled and are on by default.
- Minimal operating system.
- No locally stored enterprise data.
- Automatic Entra ID and Intune integration.
- Password-less authentication options.

## Security is on by default

Security is on by default with Windows 365 Link and includes the following features which can’t be disabled.

- A discrete [Trusted Platform Module](/windows/security/hardware-security/tpm/trusted-platform-module-overview) (TPM) 2.0 chip establishing a hardware root of trust that supports other security features like BitLocker and App Control.
- Silicon-assisted security features like [Virtualization-based Security](/windows-hardware/design/device-experiences/oem-vbs) (VBS) and [hypervisor-protected code integrity](/windows/security/hardware-security/enable-virtualization-based-protection-of-code-integrity?tabs=security) (HVCI). This feature helps protect the kernal from malicious code injection.
- Windows 365 Link follows the Unified Extensible Firmware Interface (UEFI) Secure Boot standard. This standard helps ensure only authorized firmware and software with trusted digital signatures can execute.
- [BitLocker](/windows/security/operating-system-security/data-protection/bitlocker/) is enabled during setup.
- [Application Control](/windows/security/application-security/application-control/app-control-for-business/) code integrity policies, which can’t be modified, and allow only necessary software to execute.

## Minimal software footprint

Windows 365 Link has a small, purpose-built Windows-based operating system called Windows CPC with features that help reduce the attack surface. This operating system includes only the essential components needed to securely authenticate users against Entra ID and connect them to their Windows 365 Cloud PC. To help reduce the attack surface, these features are enabled by default and can’t be turned off:

- Applicable security baseline policies, which remove the need to define and apply such configurations to the endpoint.
- Driver security. Only standard Windows class drivers and OEM-installed drivers are allowed to execute. Automatic driver acquisition is disabled.
- Admin control. All administration for Windows 365 Link is managed through Intune, and all desktop experiences occur on the Cloud PC within the Windows 365 service. As a result, there are no local users with administrative rights, and no local applications are installed on the endpoint. 
- End users don’t have access to the local storage on the Windows 365 Link hardware device, so enterprise data can’t be saved locally on the device. 

## Microsoft Entra ID

As part of the out of box experience (OOBE), Windows 365 Link is [Microsoft Entra joined](/entra/identity/devices/concept-directory-join) to your tenant and automatically [enrolled in Intune](/mem/intune-service/fundamentals/deployment-guide-enrollment-windows), giving you immediate and full management control from the beginning.

## Cloud-backed security

[Windows 365 security](../enterprise/security.md) features are enabled across the solution from the Windows 365 Link hardware device through the Windows 365 service to the Cloud PC.
Other cloud-backed security measures include:

- All connections from Windows 365 Link to Windows 365 services use Transport Layer Security (TLS) 1.2 or greater, ensuring strong protection of the communication between the hardware device and Windows 365.  
- Support for Device Health Attestation through Intune compliance policies means compliance statements about Windows 365 Link can be used in Conditional Access policies to make sure only compliant devices can connect to Windows 365 services.
- Windows 365 Link provides a password-less experience with a FIDO2 security key and web sign-in as the only credential providers available on the endpoint for sign-in.
- Windows 365 Link only connects to Cloud PCs that are configured for single sign-on (SSO).

In conjunction with specific authentication methods and conditional access policies in place on your Entra tenant, these features mean that a user should never need to enter a password to use their Windows 365 Link hardware device.

<!-- ########################## -->
## Next steps

For more information, see [Windows 365 security](../enterprise/security.md).
