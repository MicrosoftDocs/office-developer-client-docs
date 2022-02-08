---
title: "ScCountNotifications"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.ScCountNotifications
api_type:
- COM
ms.assetid: 13e80bdc-cb59-47a5-8de0-404e22f87f82
description: "Last modified: March 09, 2015"
---

# ScCountNotifications

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Determines the size, in bytes, of an array of event notifications, and validates the memory associated with the array.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
SCODE ScCountNotifications(
  int cntf,
  LPNOTIFICATION rgntf,
  ULONG FAR * pcb
);
```

## Parameters

 _cntf_
  
> [in] Count of [NOTIFICATION](notification.md) structures in the array indicated by the  _rgntf_ parameter. 
    
 _rgntf_
  
> [in] Pointer to the array of **NOTIFICATION** structures whose size is to be determined. 
    
 _pcb_
  
> [out] Optional pointer to the size, in bytes, of the array pointed to by the  _rgntf_ parameter. If NULL, **ScCountNotifications** validates the array of notifications. 
    
## Return value

S_OK
  
> Count was determined successfully.
    
MAPI_E_INVALID_PARAMETER
  
> An invalid notification was encountered.
    
## Remarks

If NULL is passed in the _pcb_ parameter, the **ScCountNotifications** function only validates the array of notifications but no counting is done; if a non-null value is passed in  _pcb_, **ScCountNotifications** determines the size of the array and stores the cause  _pcb_. The  _pcb_ parameter must be large enough to contain the entire array. 
  

