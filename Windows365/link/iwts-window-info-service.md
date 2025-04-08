---
# required metadata
title: IWTSWindowInfoService
titleSuffix:
description: Learn about the new IWTS interface IWTSWindowInfoService
keywords:
author: ribanerjee  
ms.author: ribanerjee
manager: dougeby
ms.date: 04/08/2025
ms.topic: overview
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

# IWTSWindowInfoService 

## Overview

Various functions which give information related to an RDP window that is rendered on the client machine. This allows plugin authors to query this RDP window. This allows RDP plugin authors to accurately find the current window and provide information about where to correctly render with their products.
Implemented by the RDP client.
The following enumeration, structures, and methods are relevant for this interface.

### RdpSessionType

```cpp
typedef enum RdpSessionType
{
    Desktop = 0,
    RemoteApp = 1,
} RdpSessionType;
```

Determines whether the RDP session is a desktop session or a remote app session.

### WTSWindowInfo

Contains a variety of window related information. This window should be of a process that is running in the remote and is being rendered on the client side via RDP.

```cpp
typedef struct WTSWindowInfo
{
    HWND Hwnd;
    int Height;
    int Width;
    int ViewWidth;
    int ViewHeight;
    int ViewOffsetX;
    int ViewOffsetY;
    float Scale;
} WTSWindowInfo;
```

## Inheritance

The **IWTSWindowInfoService** interface inherits from the [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) interface. **IWTSWindowInfoService** also has these types of members:

## Methods

### IWTSWindowInfoService::GetWindowInfo

```cpp
HRESULT GetWindowInfo(
  [in] HWND remoteHwnd,
  [out] WTSWindowInfo* windowInfo
);
```

**Parameters**

`[in] HWND remoteHwnd`

The HWND of the window on the client machine, that shows the remote process on the client machine.

`[out] WTSWindowInfo* windowInfo`

An instance of `WTSWindowInfoobject` corresponding to the remoteHwnd.

**Return**

Returns `S_OK` on success.

### IWTSWindowInfoService::GetRdpClientProcessId

```cpp
HRESULT GetRdpClientProcessId(
  [out, retval] unsigned long* processId
);
```

**Parameters**

`[out, retval] unsigned long* processId`

A pointer to the process ID of the RDP client process.

**Return**

Returns `S_OK` on success.

### IWTSWindowInfoService::GetRdpSessionType

```cpp
HRESULT GetRdpSessionType(
  [out, retval] RdpSessionType* sessionType
);
```

**Parameters**

`[out, retval] RdpSessionType* sessionType`

A pointer to a RdpSessionType object.

**Return**

Returns `S_OK` on success.

### IWTSWindowInfoService::SubscribeWindowChanged

```cpp
HRESULT SubscribeWindowChanged(
  [in] HWND remoteHwnd,
  [in] IWTSWindowChangedCallback* windowChanged
);
```

Monitors a window for changes and invokes a callback upon change.

**Parameters**

`[in] HWND remoteHwnd`

The HWND of the window which you want to subscribe to for changes to.

`[in] IWTSWindowChangedCallback* windowChanged`

The callback which should be invoked upon the window change. This callback is implemented by the RDP plugin.

**Return**

Returns `S_OK` on success.

### IWTSWindowInfoService::UnsubscribeWindowChanged

```cpp
HRESULT UnsubscribeWindowChanged(
  [in] HWND remoteHwnd,
  [in] IWTSWindowChangedCallback* windowChanged
);
```

Undo the SubscribeWindowChanged.

**Parameters**

`[in] HWND remoteHwnd`

The HWND of the window which you want to unsubscribe to.

`[in] IWTSWindowChangedCallback* windowChanged`

The callback which should be unregistered on window changes i.e. stop calling the callback.

**Return**

Returns `S_OK` on success.

## Requirements

| Requirement                 |  Value  |   
|-----------------------------|---------|
| Minimum supported client    |   Windows 11, version 24H2 (build 26100) or later.    |
| Target Platform             |   Windows    |
| Header                      | tsvirtualchannels.h  |
