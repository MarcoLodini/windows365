---
# required metadata
title: Windows CPC OS privacy and data
titleSuffix:
description: Learn about Windows CPC OS privacy and data
keywords:
author: ErikjeMS  
ms.author: erikje
manager: dougeby
ms.date: 04/09/2025
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

# Windows CPC OS privacy and data

Windows 365 Link comes with the Windows CPC OS preinstalled. Enterprise customers are the controllers of the Windows CPC OS diagnostic data and Microsoft processes the data in accordance with the Data Protection Addendum and product terms.

## Prerequisites

- Use a supported version of Windows CPC OS.
- The device must be joined to Microsoft Entra.

For the best experience, use the most current build of Windows CPC OS.

For information about Windows 365 Service data, see [Privacy and data in Windows 365](../enterprise/privacy-personal-data.md).

## Windows CPC OS diagnostic data and Subject Requests for the GDPR

### Introduction to Data Subject Requests (DSRs)

The EU General Data Protection Regulation (GDPR) gives rights to people (known in the regulation as data subjects) to manage the personal data that has been collected by an employer or other type of agency or organization (known as the data controller or just controller). Personal data is defined broadly under the GDPR as "any data that relates to an identified or identifiable natural person." The GDPR gives data subjects specific rights to their personal data. These rights include obtaining copies of personal data, requesting corrections to it, restricting the processing of it, deleting it, or receiving it in an electronic format so it can be moved to another controller. A formal request by a data subject to a controller to take action on their personal data is called a Data Subject Request or DSR.

Similarly, the California Consumer Privacy Act (CCPA), provides privacy rights and obligations to California consumers, including rights similar to GDPR's Data Subject Rights, such as the right to delete, access, and receive (portability) their personal information. The CCPA also provides for certain disclosures, protections against discrimination when electing exercise rights, and "opt-out/opt-in" requirements for certain data transfers classified as "sales". This document guides you to information on the completion of Data Subject Requests (DSRs) under the GDPR and CCPA using Microsoft products and services.

The guide discusses how to use Microsoft products, services, and administrative tools to help our controller customers find and act on personal data to respond to DSRs. Specifically,  how to find, access, and act on personal data in the Windows CPC OS diagnostic data that is collected by Microsoft when the Windows CPC OS diagnostic data processor configuration is enabled. Here’s a quick overview of the processes outlined in this guide:

1. **Access**: Retrieve Windows CPC OS diagnostic data associated with a data subject and if requested, make a copy of it that can be available to the data subject.
2. **Delete**: Permanently remove Windows CPC OS diagnostic data associated with a data subject.
3. **Export**: Provide an electronic copy (in a machine-readable format) of Windows CPC OS diagnostic data to the data subject.

Each section in this guide outlines the technical procedures that a data controller organization can take to respond to a DSR for Windows CPC OS diagnostic data that is collected by Microsoft when the Windows CPC OS diagnostic data processor configuration is enabled.

### Terminology

The following list provides definitions of terms that are relevant to this guide.

- **Controller**: The natural or legal person, public authority, agency or other body which, alone or jointly with others, determines the purposes and means of the processing of personal data; where the purposes and means of such processing are determined by Union or Member State law, the controller, or the specific criteria for its nomination may be provided for by Union or Member State law.
- **Personal data and data subject**: Any information relating to an identified or identifiable natural person (‘data subject'); an identifiable natural person is one who can be identified, directly or indirectly, in particular by reference to an identifier such as a name, an identification number, location data, an online identifier or to one or more factors specific to the physical, physiological, genetic, mental, economic, cultural, or social identity of that natural person.
- **Processor**: A natural or legal person, public authority, agency, or other body that processes personal data on behalf of the controller.
- **Customer Data**: All data, including all text, sound, video, or image files, and software, that are provided to Microsoft by, or on behalf of, a customer through use of the enterprise service.
- **Windows CPC OS diagnostic data**: Technical data from Windows 365 Link about the device and how Windows CPC OS and related software are performing. It's used to keep Windows CPC OS devices up to date, secure, reliable, performant, and make product improvements. Some examples of Windows CPC OS diagnostic data are the type of hardware being used, and reliability information on device drivers. Some Windows CPC OS components and plugin, connect to Microsoft services directly, but the data they exchange isn't Windows CPC OS diagnostic data. Note: By default, the Windows CPC OS collects ‘Basic/Required’ diagnostic data to keep the OS secure, up to date, and working as expected. An IT admin can manage these settings through Intune and can choose devices to send "Optional" diagnostics data.

### Windows CPC diagnostic data

> [!IMPORTANT]  
> By default, the Windows CPC OS collects "Basic/Required" diagnostic data to keep the OS secure, up to date, and working as expected. An IT admin can manage these settings through Intune and can choose devices to send "Optional" diagnostics data.

Microsoft provides Enterprise customer’s tenant admin with the ability to access, delete, and export Windows CPC OS diagnostic data associated with a user’s use of the devices enabled with the Windows CPC OS diagnostic data.

> [!IMPORTANT]  
> Some Windows CPC OS diagnostic data is only associated with a device identifier and isn't associated with a specific user. This type of device level data is deleted from our systems within 30 days.

The ability to rectify Windows CPC OS diagnostic data isn't supported. Windows CPC OS diagnostic data constitutes factual actions conducted within Windows CPC OS, and modifications to such data would compromise the historical record of actions, increasing security risks and harming reliability.

The next section provides steps on how to execute a data subject request for Windows CPC OS diagnostic data that is associated with a Microsoft Entra user ID.

### Executing DSRs against Windows CPC OS diagnostic data

Microsoft provides the ability to access, delete, and export certain Windows CPC OS diagnostic data through the Azure portal, and also directly via preexisting application programming interfaces (APIs).

### Step 1: Access

Microsoft provides a way for the tenant administrator within your organization to access Windows CPC OS diagnostic data associated with a particular user’s use of a device. The data retrieved for an access request will be provided, via export, in a machine-readable format and will be provided in files that allow the user to know which devices and services the data is associated with. As noted previously, the data retrieved won't include data that may compromise the security or stability of the Windows 365 Link device.

The Azure portal provides the enterprise customer’s tenant administrator the capability to manage DSR access requests. Azure DSR, Part 2, Step 3: Export, describes how to execute a DSR access request for Windows CPC OS diagnostic data, via export, through the Azure portal.

### Step 2: Delete

Microsoft provides a way to execute user-based DSR delete requests based on a particular user's Microsoft Entra object.

For user-based delete requests, Microsoft offers two solutions. There's a portal experience providing the enterprise customer’s tenant administrator the capability to manage DSR delete requests. Azure DSR, Part 1, Step 5: Delete, describes how to execute a DSR delete request for Windows CPC OS diagnostic data through the Azure portal by deleting a user and associated data.

Microsoft also provides the ability to delete users, which in turn deletes Windows CPC OS diagnostic data, directly via a preexisting application programming interface (API). Details are described in the API reference documentation.

> [!IMPORTANT]  
> Deleting collected data doesn't stop further collection from the device. To turn off data collection follow the procedure described in the respective service's reference documentation.

### Step 3: Export

The tenant administrator is the only person within your organization who can access Windows CPC OS diagnostic data associated with a particular user's use of a Windows 365 Link enabled with the Windows CPC OS diagnostic data processor configuration. The data retrieved for an export request will be provided in a machine-readable format and will be provided in files that allow the user to know which devices and services the data is associated with. As noted previously, the data retrieved won't include data that may compromise the security or stability of the Windows 365 Link. Azure DSR, Part 2, Step 3: Export, describes how to execute a DSR export request for Windows CPC OS diagnostic data through the Azure portal.

Microsoft also provides the ability to export Windows CPC OS diagnostic data directly via a preexisting application programming interface (API). Details are described in the API reference documentation.

### Notify us about exporting or deleting issues

If you run into issues while exporting or deleting Windows CPC OS diagnostic data from the Azure portal, go to the Azure portal **Help + Support** blade and submit a new ticket under **Subscription Management** > **Privacy and compliance requests for Subscriptions** > **Privacy Blade and GDPR Requests**.

> [!NOTE]  
> It can take up to five days to complete a Windows CPC OS diagnostic data export request. If you experience issues, please allow at least seven days before opening a support ticket.

<!-- ########################## -->
## Next steps

[Privacy, customer data, and customer content in Windows 365](../privacy-personal-data.md)
