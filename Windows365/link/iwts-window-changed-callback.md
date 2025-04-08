---
# required metadata
title: IWTSWindowChangedCallback
titleSuffix:
description: Learn about the new IWTS interface IWTSWindowChangedCallback
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

# IWTSWindowChangedCallback
## Overview
A callback that is invoked whenever an RDP window that is subscribed to and it changes. The RDP plugin should implement the interface IWTSWindowChangedCallback.

## Inheritance
**IWTSWindowChangedCallback** interface inherits from the [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) interface. IWTSWindowChangedCallback also has these types of members:

## Methods

### IWTSWindowChangedCallback::WindowChanged

```cpp
HRESULT WindowChanged(
    [in] const WTSWindowInfo* windowInfo
);
```

The callback function which is invoked when a remote window that is subscribed to changes. 

**Parameters**

`[in] const WTSWindowInfo* windowInfo`

A pointer to a `WTSWindowInfo` object of the corresponding remote window.

**Return**

Returns `S_OK` on success.

## Requirements

| Requirement                 |  Value  |   
|-----------------------------|---------|
| Minimum supported client    |   Windows 11, version 24H2 (build 26100) or later.    |
| Target Platform             |   Windows    |
| Header                      | tsvirtualchannels.h  |
