---
title: "ScCopyNotifications"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.ScCopyNotifications
api_type:
- COM
ms.assetid: ac31cf65-a2bc-4c8e-91a4-d2903aa98776
description: "Copies a group of event notifications to a single block of memory."
---

# ScCopyNotifications

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Copies a group of event notifications to a single block of memory. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
SCODE ScCopyNotifications(
  int cntf,
  LPNOTIFICATION rgntf,
  LPVOID pvDst,
  ULONG FAR * pcb
);
```

## Parameters

 _cntf_
  
> [in] Count of [NOTIFICATION](notification.md) structures in the array indicated by the  _rgntf_ parameter. 
    
 _rgntf_
  
> [in] Pointer to an array of **NOTIFICATION** structures defining the event notifications to be copied. 
    
 _pvDst_
  
> [out] Pointer to the returned notifications. 
    
 _pcb_
  
> [out] Optional pointer to a variable where the size, in bytes, of the array pointed to by the  _rgntf_ parameter is stored. If not NULL, the  _pcb_ parameter is set to the number of bytes stored in the _pvDst_ parameter. 
    
## Return value

S_OK
  
> Event notifications were copied successfully.
    
E_INVALIDARG
  
> An invalid notification was encountered.
    
## Remarks

If NULL is passed in the _pcb_ parameter, no copying is performed; if a non-null value is passed in  _pcb_, the **ScCopyNotifications** function copies the size of the array and the array itself to a single block of memory. If  _pcb_ is not NULL, it is set to the number of bytes stored in the _pvDst_ parameter. The  _pvDst_ parameter must be large enough to contain the entire array. 
  

