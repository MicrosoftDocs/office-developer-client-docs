---
title: "RebaseTaskProgress"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
 
 
localization_priority: Normal
ms.assetid: 8b8368d2-b04b-42a5-fdc3-955fc873c2f5
description: "Reports progress for enumeration and rebasing of appointments."
---

# RebaseTaskProgress

Reports progress for enumeration and rebasing of appointments.
  
## Quick Info

|||
|:-----|:-----|
|Header file:  <br/> |tzmovelib.h  <br/> |
|Implemented by:  <br/> |MAPI client applications  <br/> |
|Called by:  <br/> |Outlook rebasing object  <br/> |
|Pointer type:  <br/> |**PFNREBASETASKPROGRESS** as defined in tzmovelib.h  <br/> |
   
```
void STDAPICALLTYPE RebaseTaskProgress(  
    ULONG ulMin, 
    ULONG ulMax, 
    ULONG ulCur, 
    REBASE_APPT_STATE State, 
    const SRow* pRowCur); 

```

## Parameters

 _ulMin_
  
> [in] The low end of the range of appointments being processed. It is usually zero.
    
 _ulMax_
  
> [in] The high end of the range of appointments being processed. It is usually the number of items in the calendar folder being processed.
    
 _ulCur_
  
> [in] The current item being processed.
    
 _State_
  
> [in] A value that indicates the status of the item being processed. The enumeration **REBASE_APPT_STATE** is defined in tzmovelib.h.  _State_ is one of the following values: 
    
    - **REBASE_APPT_STATE_SCANNING_EXAMINING** —Scanning and examining an item. 
    
    - **REBASE_APPT_STATE_SCANNING_FOUND** —Scanning and found an item. 
    
    - **REBASE_APPT_STATE_BEGIN** —Fixing and starting an item. 
    
    - **REBASE_APPT_STATE_REBASING** —Fixing and adjusting an item. 
    
    - **REBASE_APPT_STATE_SENDING** —Fixing and sending a meeting update. 
    
    - **REBASE_APPT_STATE_DONE** —Fixing and done with an item. 
    
 _pRowCur_
  
> [in] A pointer to an **[SRow](http://msdn.microsoft.com/library/369c2d5c-8c2b-4314-9cb2-aaa89580aa2b%28Office.15%29.aspx)** structure that describes the item being scanned or fixed. 
    
## Return Values

S_OK if the call succeeded; otherwise, an error code.
  
## Remarks

MAPI client applications that use the [IOlkApptRebaser](iolkapptrebaser.md) interface implement this function to track item processing. 
  
## See also

#### Concepts

[About rebasing calendars programmatically for Daylight Saving Time](about-rebasing-calendars-programmatically-for-daylight-saving-time.md)

