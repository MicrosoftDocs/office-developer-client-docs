---
title: "IOlkApptRebaserBeginEnumerateAppointments"
ms.author: soliver
author: soliver
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 8946703a-aaa8-6b3f-aa68-931365db620d
description: "Begins a task for appointment enumeration in a calendar folder to find the appointments that need rebasing."
---

# IOlkApptRebaser::BeginEnumerateAppointments

Begins a task for appointment enumeration in a calendar folder to find the appointments that need rebasing.
  
## Quick Info

See [IOlkApptRebaser](iolkapptrebaser.md).
  
```
HRESULT BeginEnumerateAppointments( 
    PFNREBASETASKPROGRESS pfnProgress, 
    void **ppContext);
```

## Parameters

 _pfnProgress_
  
> [in] Optional. A pointer to a rebase task progress function to receive progress. **PFNREBASETASKPROGRESS** is defined in tzmovelib.h. 
    
 _ppContext_
  
> [out] Required. A pointer to a pointer to the returned context. This context will be passed to [IOlkApptRebaser::EndEnumerateAppointments](iolkapptrebaser-endenumerateappointments.md).
    
## Return Values

S_OK if the call succeeded; otherwise, an error code.
  
## Remarks

This task runs on a new thread.
  
## See also

#### Concepts

[About rebasing calendars programmatically for Daylight Saving Time](about-rebasing-calendars-programmatically-for-daylight-saving-time.md)

