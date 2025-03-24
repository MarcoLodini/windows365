---
# required metadata
title: Windows 365 Link sign-in methods
titleSuffix:
description: Learn about Windows 365 Link sign-in methods
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

# Windows 365 Link sign-in methods

Windows 365 Link supports two methods for user sign-in: Web sign-in and FIDO2 security keys.

## Web sign-in

Web sign-in is a web-based sign-in experience for Microsoft Entra ID tenants and Microsoft Entra joined devices. You can configure your Microsoft Entra tenant to support this sign-in method for Windows 365 Link without the need to configure anything on the device.

You can configure the following Authentication Methods in your Microsoft Entra tenant:

- User name and password.
- Phone sign-in with Microsoft Authenticator.
- FIDO2 security key.
- Passkey on another device through cross device authentication.

For full information on the available authentication methods, including recommendations for best security implementation, see [What authentication and verification methods are available in Microsoft Entra ID?]( /en-us/entra/identity/authentication/concept-authentication-methods).

### Using web sign-in

1. On the Windows 365 Link sign-in screen, select the globe icon.
2. Type your User Principal Name (UPN) (for example, John@contoso.com) and select the arrow.
3. Based on the authentication methods configured on your tenant, follow the Microsoft Entra web sign-in process.

#### Third-party identity providers

Third party identity providers can be used for signing in to Windows 365 Link. However, some limitations can arise if the third party identity provider uses [custom controls](/entra/identity/conditional-access/controls) to integrate with your tenant. Custom controls:

- Can’t be used to satisfy multifactor authentication claim requirements
- Don’t support Intune device enrollment.
- Don’t support joining devices to Microsoft Entra ID.

Microsoft Entra’s [external authentication method](/entra/identity/authentication/how-to-authentication-external-method-manage) can be used instead of custom controls for a better Windows 365 Link web sign-in experience.

#### Certificate-based authentication (CBA)

[Microsoft Entra certificate-based authentication](/entra/identity/authentication/concept-certificate-based-authentication) is currently not supported as part of web sign-in on Windows 365 Link.

## FIDO2 security key

FIDO2 security key lets a user sign-in with a passkey saved on a FIDO2 security key. Enabling this sign-in method may require configuration in your environment.

If the Windows 365 Link sign-in screen doesn’t show two icons (a security key and a globe) at the bottom, then the device isn’t configured to use FIDO2 security keys. For more information, see [Enable FIDO2 security key sign-in to Windows 10 and 11 devices with Microsoft Entra ID](/entra/identity/authentication/howto-authentication-passwordless-security-key-windows).  

### Using FIDO2 security key

1. To start the FIDO2 security key sign in process, you can either:

- Insert the security key into the USB port. Windows 365 Link automatically switches to this credential provider. 
- Select the security key icon.

2. In the prompt, enter your PIN.
3. When prompted, touch the security key to prove presence.
4. The sign-in process completes and you’re connected to your Cloud PC.

### Multiple Microsoft Entra accounts on one FIDO2 security key

If a FIDO2 security key contains more than one Microsoft Entra account, the last account added to the FIDO2 security key is automatically selected for sign-in or unlocking using this credential provider.

If supporting a security key containing multiple keys is a required scenario and you want to avoid the forced key selection, you can instead use the Web sign-in credential provider. In this case, select security key when prompted for the authentication method. This option lets you select a specific Microsoft Entra account on the FIDO2 security key.

<!-- ########################## -->
## Next steps

[Sign in to, sign out, or lock your Windows 365 Link](sign-in.md)
 