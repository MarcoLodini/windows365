---
# required metadata
title: Secure out-of-process plugin
titleSuffix:
description: Learn about the secure out-of-process plugin for Windows 365 Link
keywords:
author: ribanerjee  
ms.author: ribanerjee
manager: dougeby
ms.date: 04/08/2025
ms.topic: how-to
ms.service: windows-365-link
ms.subservice:
ms.localizationpriority: high
ms.assetid: 

# optional metadata

#ROBOTS:
#audience:

ms.reviewer: ribanerjee
ms.suite: ems
search.appverid: MET150
#ms.tgt_pltfrm:
ms.custom: intune-azure; get-started; intro-hub-or-landing
ms.collection:
- M365-identity-device-management
- tier2
---

# Secure out-of-process plugin for Windows 365 Link (preview)

## Introduction

### What is a Remote Desktop plugin?

A Remote Desktop plugin is an extension or add-on that enhances the functionality of Microsoft Remote Desktop (RDP) clients, typically in third-party applications. For example, [Teams VDI Plugin](/microsoftteams/vdi-2) which is designed to optimize the performance of Teams when running in virtualized environments.
**For Windows 365 Link, these plugins must comply with a new architecture detailed in this document. If you represent an ISV that needs a Remote Desktop plugin to work with Link, please [complete and submit this form](https://forms.microsoft.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR5TElPlHy6hJpLhhqUqVoJpUNE9DRDlYTlhPTEhJS0lONDk2TzNLTkpQNy4u).**

This feature is in [public preview](../public-preview.md).

### What is an out-of-process Remote Desktop Plugin? 
Traditional RDP plugins are loaded into the same process as the RDP client. As seen in the following diagram, the `RDPClientProcess.exe` loads the different RDP plugin dlls. Once loading is done, the plugin becomes part of the `RDPClientProcess.exe`.
![in process plugin model](./media/secure-out-process-plugin/inproc.png "in process plugin model")

In the out-of-process model,
1. The RDP client process loads the RDP plugins out-of-process, that is, as an independent process separate from the RDP client and
2. Limit the plugin's access to the wider Windows operating system by enforcing process isolation using [AppContainers](/windows/win32/secauthz/appcontainer-isolation).

## Out-of-process plugin loading architecture
The following diagram shows a high-level explanation of how the RDP clients interact with the RDP plugins in an out-of-process model.

![out-of-process plugin model](./media/secure-out-process-plugin/outofproc.png "out-of-process plugin model")
1. The RDP plugins can be thought of as COM servers and RDP clients are COM clients.
2. The RDP plugins are now independent processes running in App Isolation. The RDPClientProcess.exeloads the plugins using COM's [CoCreateInstance API](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).
3. The RDP plugin authors don't have to change the core business logic present in the dlls. They just need to package the plugin as an [MSIX](/windows-365/link/secure-out-process-plugin#msix). Thus, plugin authors have to make minimal changes to the RDP plugin code.

## Implementation details
There are three parties involved when plugins are used in an RDP connection.
1. The RDP client (for example, [Windows App](/windows-app/overview)).
2. The RDP plugin.
3. The application for which the plugin is written (for example, [Teams application](https://www.microsoft.com/microsoft-teams/group-chat-software)).

For example, consider a situation, when a user uses Azure Virtual desktop to connect to a virtual desktop and uses Teams application running in the virtual desktop. Here the Azure Virtual Desktop is the RDP client (client application), the [Teams VDI plugin](/microsoftteams/new-teams-vdi-requirements-deploy) is the RDP plugin and the Teams is the remote application running in the virtual desktop is the server application.

We have a complete working example [here](https://github.com/microsoft/SampleOutOfProcRdpPlugin/tree/main). In this example, we go into implementation details using an example RDP client, RDP plugin and a sample application running in the remote virtual machine.

### What do plugin authors have to do?
All RDP plugins work through COM communications. The RDP plugin is the COM server, and the RDP client is the COM client (For more information, see [COM clients and COM servers](/windows/win32/com/com-clients-and-servers)). Both the COM client (RDP client) and COM server (RDP Plugin) are in the client machine.
There are two main tasks that the plugin authors need to complete-
1. Define the functions of the interfaces declared in [tsvirtualchannels documentation](/windows/win32/api/tsvirtualchannels/). Plugin authors need not define every single function but only the ones that are in use.
2. Package/distribute the RDP plugin as an [MSIX](/windows-365/link/secure-out-process-plugin#msix). Currently MSIX is the only way of packaging applications which supports [App Isolation](/windows-365/link/secure-out-process-plugin#app-isolation), [COM](/windows-365/link/secure-out-process-plugin#component-object-model) and [Package Identity](/windows-365/link/secure-out-process-plugin#package-identity). There are some important details that need to be kept in mind while packaging the app. These details are addressed using an example [here](https://github.com/microsoft/SampleOutOfProcRdpPlugin/blob/main/SamplePluginMsix/README.md).

### What do the RDP clients have to do?
At a high level, it's the RDP client's responsibility to 
1. Discover and load the RDP plugins into memory.
2. Implement client-side interfaces like `IWTSWindowInfoService`.

Once, the RDP client process is launched, it should have the code to,
1. Discover the plugins using `AppExtensionCatalog::Open("com.microsoft.rdp.plugin.wtsplugin")`. For more information, see [app extensions documentation](/uwp/api/windows.applicationmodel.appextensions.appextensioncatalog.open).
2. Get the COM class id of the discovered plugins.
3. Create the plugin factory's COM object using [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) 
Create the actual plugin by using the plugin factory's `CreatePluginAPI` (defined in the RDP plugin itself).

### What does the RDP server application have to do to send/receive data?
The server application can use the [WTSVirtualChannelOpenEx](/windows/win32/api/wtsapi32/nf-wtsapi32-wtsvirtualchannelopenex) API to open a dynamic virtual channel to the RDP plugin running in the client machine by passing the `WTS_CHANNEL_OPTION_DYNAMIC` flag. This API opens a duplex channel between the RDP client and server application.

It can then write data to the virtual channel using the [WTSVirtualChannelWrite](/windows/win32/api/wtsapi32/nf-wtsapi32-wtsvirtualchannelwrite) API and similarly read data from the channel using the [WTSVirtualChannelRead](/windows/win32/api/wtsapi32/nf-wtsapi32-wtsvirtualchannelread) API.
The prerequisites of opening this dynamic virtual channel are:
1. An RDP connection must exist between the RDP client and server
2. The RDP plugin must already be loaded in the client machine

## Technologies that are used/good to know
Since creating and using RDP plugins in an out-of-process manner requires the knowledge of several technologies, it's better to have some basic understanding of these before proceeding with the actual RDP plugin development and usage.

### [MSIX](/windows/msix/overview)
MSIX is a modern Windows application packaging format introduced by Microsoft to replace traditional EXE, MSI, and AppX installers. 

### [AppContainer](/windows/msix/msix-container)
A runtime security sandbox that isolates the running application in it from the rest of the system, preventing unauthorized access to resources, sensitive data, and other processes. 

### [Package Identity](/windows/apps/desktop/modernize/package-identity-overview)
A unique identifier assigned to the AppContainer application that allows Windows to enforce security policies, resource access controls, and application isolation. Windows container technology uses this identity as a primary key to identify which application has what resource access.

### [App Isolation](/windows/win32/secauthz/app-isolation-overview)
1. AppContainers + tools that allow for easy development. Windows provides tools like [Application Capability Profiler](/windows/win32/secauthz/app-isolation-capability-profiler) which automatically tells the [capabilities of application](/windows/uwp/packaging/app-capability-declarations) instead of manually finding them by looking at the code.
2. Provides [COM](/windows/win32/com/component-object-model--com--portal) capabilities within the application which lets application authors declare their COM classes to be consumed by other applications providing seamless interop.

### [App Extensions](/windows/msix/desktop/extend-overview)
App Extension are similar to plugins which allow developers to extend the functionalities of an existing application.

### [Component Object Model](/windows/win32/com/component-object-model--com--portal)
Applications can expose interfaces in a platform independent manner without having to expose the "how's" of the functionality. The RDP plugins interact with the RDP client using this model by exposing interfaces.

### RDP channel
An RDP channel is a logical communication stream between the RDP plugin and the RDP server (like Remote Desktop Services Host). It allows custom data to be sent back and forth alongside the regular RDP session—separate from screen, keyboard, or mouse data.

### [Dynamic Virtual Channels](/windows/win32/termserv/dynamic-virtual-channels)
Static (traditional) Virtual Channels allow lossless communication between client and server components over the main RDP data connection. Dynamic Virtual Channels are an improved version, but the core functionality is the same.

### [Fast Rundown](/windows/win32/api/objidl/nn-objidl-ifastrundown)
COM Fast Rundown is a setting in COM server registration (search for `COMGLB_FAST_RUNDOWN` [here](/windows/win32/api/objidl/nn-objidl-iglobaloptions)) that tells Windows how to handle the lifetime of an out-of-process COM server. Specifically, it can speed up COM shutdown behavior by allowing the COM runtime to aggressively terminate the server when no more clients are connected. It can still take up to 10 seconds.

### [Marshalling/unmarshalling](/windows/win32/com/inter-object-communication)
A mechanism used for transferring data/COM objects during an out-of-process communication between COM client and the COM server across address spaces, such as between different processes.