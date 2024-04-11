---
title: "IOlkApptRebaserEndRebaseAppointments"
manager: lindalu
ms.date: 11/16/2014
ms.audience: Developer
ms.topic: reference
ms.localizationpriority: medium
ms.assetid: e47d5a8d-6a13-f430-fbfd-00df04b4a006
description: "Waits for appointment rebasing to complete and retrieves the results."
---

# IOlkApptRebaser::EndRebaseAppointments

Waits for appointment rebasing to complete and retrieves the results.
  
## Quick info

See [IOlkApptRebaser](iolkapptrebaser.md).
  
```cpp
HRESULT EndRebaseAppointments( 
    void *pContext, 
    HRESULT *phResult);
```

## Parameters

_pContext_
  
> [in] Required. A pointer to the context obtained from a call to [IOlkApptRebaser::BeginRebaseAppointments](iolkapptrebaser-beginrebaseappointments.md).
    
_phResult_
  
> [out] Required. A pointer to an **HRESULT** to retrieve the result of the rebasing operation. 
    
## Return values

S_OK if the call succeeded; otherwise, an error code.
  
## See also

- [About rebasing calendars programmatically for Daylight Saving Time](about-rebasing-calendars-programmatically-for-daylight-saving-time.md)

