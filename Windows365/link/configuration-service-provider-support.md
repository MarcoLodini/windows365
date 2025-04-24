---
# required metadata
title: Supported configuration service provider policies for Windows 365 Link
titleSuffix:
description: Learn about the supported configuration service provider policies for Windows 365 Link
keywords:
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/24/2025
ms.topic: overview
ms.service: windows-365-link
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
- essentials-get-started
---

# Supported configuration service provider policies for Windows 365 Link

Windows 365 Link runs a small purpose-built Windows based operating system called Windows CPC. Therefore, device configuration for Windows 365 Link follows the same process as Windows in general with two main differences.

- Windows 365 Link can only be Entra joined, so Active Directory Group Policy isn’t supported for the device.
- Windows 365 Link supports a subset of Windows configuration service provider (CSP) policies.

There are no new CSPs or policies specifically created for Windows 365 Link.

While a CSP in general may be supported, specific policies within it may cover functionality that isn’t enabled on the device. So, certain policies within these supported CSPs may have no effect when applied to a Windows 365 Link device.

## Policy CSP areas supported on for Windows 365 Link

- [Audit](/windows/client-management/mdm/policy-csp-audit)
- [Authentication](/windows/client-management/mdm/policy-csp-authentication)
- [BitLocker](/windows/client-management/mdm/policy-csp-bitlocker)
- [Bluetooth](/windows/client-management/mdm/policy-csp-bluetooth)
- [Camera](/windows/client-management/mdm/policy-csp-camera)
- [CloudDesktop](/windows/client-management/mdm/policy-csp-clouddesktop)
- [Connectivity](/windows/client-management/mdm/policy-csp-connectivity)
- [Defender](/windows/client-management/mdm/policy-csp-defender)
- [DeliveryOptimization](/windows/client-management/mdm/policy-csp-deliveryoptimization)
- [DeviceGuard](/windows/client-management/mdm/policy-csp-deviceguard)
- [DeviceHealthMonitoring](/windows/client-management/mdm/policy-csp-devicehealthmonitoring)
- [DeviceLock](/windows/client-management/mdm/policy-csp-devicelock)
- [DmaGuard](/windows/client-management/mdm/policy-csp-dmaguard)
- [Licensing](/windows/client-management/mdm/policy-csp-licensing)
- [LocalPoliciesSecurityOptions](/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions)
- [MemoryDump](/windows/client-management/mdm/policy-csp-memorydump)
- [Power](/windows/client-management/mdm/policy-csp-power)
- [Privacy](/windows/client-management/mdm/policy-csp-privacy)
- [RemoteDesktopServices](/windows/client-management/mdm/policy-csp-remotedesktopservices)
- [Security](/windows/client-management/mdm/policy-csp-security)
- [SmartScreen](/windows/client-management/mdm/policy-csp-smartscreen)
- [System](/windows/client-management/mdm/policy-csp-system)
- [TimeLanguageSettings](/windows/client-management/mdm/policy-csp-timelanguagesettings)
- [Update](/windows/client-management/mdm/policy-csp-update)
- [VirtualizationBasedTechnology](/windows/client-management/mdm/policy-csp-virtualizationbasedtechnology)
- [Wifi](/windows/client-management/mdm/policy-csp-wifi)

## Other CSPs supported on Windows 365 Link

- [BitLocker](/windows/client-management/mdm/bitlocker-csp)
- [CertificateStore](/windows/client-management/mdm/certificatestore-csp)
- [CleanPC](/windows/client-management/mdm/cleanpc-csp)
- [ClientCertificateInstall](/windows/client-management/mdm/clientcertificateinstall-csp)
- [CloudDesktop](/windows/client-management/mdm/clouddesktop-csp)
- [DeclaredConfiguration](/windows/client-management/mdm/declaredconfiguration-csp)
- [Defender](/windows/client-management/mdm/defender-csp)
- [DevDetail](/windows/client-management/mdm/devdetail-csp)
- [DeviceManageability](/windows/client-management/mdm/devicemanageability-csp)
- [DevicePreparation](/windows/client-management/mdm/devicepreparation-csp)
- [DeviceStatus](/windows/client-management/mdm/devicestatus-csp)
- [DevInfo](/windows/client-management/mdm/devinfo-csp)
- [DiagnosticLog](/windows/client-management/mdm/diagnosticlog-csp)
- [DMAcc](/windows/client-management/mdm/dmacc-csp)
- [DMClient](/windows/client-management/mdm/dmclient-csp)
- [DMSessionActions](/windows/client-management/mdm/dmsessionactions-csp)
- [EnrollmentStatusTracking](/windows/client-management/mdm/enrollmentstatustracking-csp)
- [Firewall](/windows/client-management/mdm/firewall-csp)
- [HealthAttestation](/windows/client-management/mdm/healthattestation-csp)
- [LangaugePackManagement](/windows/client-management/mdm/language-pack-management-csp)
- [NetworkProxy](/windows/client-management/mdm/networkproxy-csp)
- [NetworkQosPolicy](/windows/client-management/mdm/networkqospolicy-csp)
- [NodeCache](/windows/client-management/mdm/nodecache-csp)
- [Personalization](/windows/client-management/mdm/personalization-csp)
- [Provisioning](/windows/client-management/mdm/provisioning-csp)
- [Reboot](/windows/client-management/mdm/reboot-csp)
- [RemoteFind](/windows/client-management/mdm/remotefind-csp)
- [RemoteWipe](/windows/client-management/mdm/remotewipe-csp)
- [RootCATrustedCertificates](/windows/client-management/mdm/rootcacertificates-csp)
- [TenantLockdown](/windows/client-management/mdm/tenantlockdown-csp)
- [TPMPolicy](/windows/client-management/mdm/tpmpolicy-csp)
- [WiFi](/windows/client-management/mdm/wifi-csp)
- [WindowsAdvancedThreatProtection](/windows/client-management/mdm/windowsadvancedthreatprotection-csp)
- [WindowsLicensing](/windows/client-management/mdm/windowslicensing-csp)
- [WiredNetwork](/windows/client-management/mdm/wirednetwork-csp)

<!-- ########################## -->
## Next steps

[Make sure your environment meets all requirements](requirements.md).
