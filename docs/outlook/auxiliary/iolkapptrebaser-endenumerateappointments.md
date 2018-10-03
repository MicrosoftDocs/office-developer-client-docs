---
title: "IOlkApptRebaserEndEnumerateAppointments"
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
localization_priority: Normal
ms.assetid: bc4506c7-7a4f-940d-d0a6-e0fab4561a88
description: "Waits for appointment enumeration in a calendar folder to complete and returns a list of appointments that need rebasing."
---

# IOlkApptRebaser::EndEnumerateAppointments

Waits for appointment enumeration in a calendar folder to complete and returns a list of appointments that need rebasing.
  
## Quick info

See [IOlkApptRebaser](iolkapptrebaser.md).
  
```cpp
HRESULT EndEnumerateAppointments( 
    void *pContext, 
    HRESULT *phResult, 
    MAPIERROR **ppError, 
    SRowSet **ppRows);
```

## Parameters

_pContext_
  
> [in] Required. A pointer to the context obtained from a prior call to [IOlkApptRebaser::BeginEnumerateAppointments](iolkapptrebaser-beginenumerateappointments.md).
    
_phResult_
  
> [out] Required. A pointer to an **HRESULT** to retrieve the results of the enumeration operation. 
    
_ppError_
  
> [out] Optional. A pointer to a pointer to a **MAPIERROR** structure to retrieve extended error information. 
    
_ppRows_
  
> [out] Required. A pointer to a pointer to an [SRowSet](https://msdn.microsoft.com/library/7e3761be-afd6-46cb-9a08-25e9016c1241%28Office.15%29.aspx) structure that describes the appointments that need rebasing. This structure will usually be passed to [IOlkApptRebaser::BeginRebaseAppointments](iolkapptrebaser-beginrebaseappointments.md).
    
## Return values

S_OK if the call succeeded; otherwise, an error code.
  
## See also

- [About rebasing calendars programmatically for Daylight Saving Time](about-rebasing-calendars-programmatically-for-daylight-saving-time.md)

