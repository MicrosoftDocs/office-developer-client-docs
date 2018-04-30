---
title: "RebaseTaskComplete"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 2de5c77c-3fac-cfb6-3719-68df4013cf11
description: "Reports completion for rebasing of appointments."
---

# RebaseTaskComplete

Reports completion for rebasing of appointments.
  
## Quick Info

|||
|:-----|:-----|
|Header file:  <br/> |tzmovelib.h  <br/> |
|Implemented by:  <br/> |MAPI client applications  <br/> |
|Called by:  <br/> |Outlook rebasing object  <br/> |
|Pointer type:  <br/> |**PFNREBASETASKCOMPLETE** as defined in tzmovelib.h  <br/> |
   
```
void STDAPICALLTYPE RebaseTaskComplete(  
    ULONG ulRowIndex, 
    const SRow* pRowCur, 
    HRESULT hrResult, 
    BOOL fModified, 
    BOOL fSentUpdate, 
    const MAPIERROR* pError); 

```

## Parameters

 _ulRowIndex_
  
> [in] The row that was processed. This index refers to the **[SRowSet](http://msdn.microsoft.com/library/7e3761be-afd6-46cb-9a08-25e9016c1241%28Office.15%29.aspx)** structure passed to [IOlkApptRebaser::BeginRebaseAppointments](iolkapptrebaser-beginrebaseappointments.md).
    
 _pRowCur_
  
> in] A pointer to an **[SRow](http://msdn.microsoft.com/library/369c2d5c-8c2b-4314-9cb2-aaa89580aa2b%28Office.15%29.aspx)** structure describing the item that was processed. 
    
 _hrResult_
  
> [in] An **HRESULT** indicating the result of the rebasing operation. 
    
 _fModified_
  
> [in] Specifies whether the item was modified.
    
 _fSentUpdate_
  
> [in] Specifies whether a meeting update message was sent. 
    
 _pError_
  
> [in] A pointer to a **MAPIERROR** structure with extended error information. 
    
## Return Values

S_OK if the call succeeded; otherwise, an error code.
  
## Remarks

MAPI client applications that use the [IOlkApptRebaser](iolkapptrebaser.md) interface implement this function to track completion of item updates. 
  
## See also

#### Concepts

[About rebasing calendars programmatically for Daylight Saving Time](about-rebasing-calendars-programmatically-for-daylight-saving-time.md)

