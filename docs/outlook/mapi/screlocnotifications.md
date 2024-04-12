---
title: "ScRelocNotifications"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.ScRelocNotifications
api_type:
- COM
ms.assetid: 22de5d38-7be6-48b3-90a7-bc553dcdb042
description: "Adjusts a pointer within a specified event notification array for Outlook 2013 or Outlook 2016."
---

# ScRelocNotifications

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Adjusts a pointer within a specified event notification array. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
SCODE ScRelocNotifications(
  int cntf,
  LPNOTIFICATION rgntf,
  LPVOID pvBaseOld,
  LPVOID pvBaseNew,
  ULONG FAR * pcb
);
```

## Parameters

 _cntf_
  
> [in] Count of [NOTIFICATION](notification.md) structures in the array indicated by the  _rgntf_ parameter. 
    
 _rgntf_
  
> [in] Pointer to the array of **NOTIFICATION** structures defining event notifications within which a pointer is to be adjusted. 
    
 _pvBaseOld_
  
> [in] Pointer to the original base address of the array indicated by the  _rgntf_ parameter. 
    
 _pvBaseNew_
  
> [in] The location to which **ScRelocNotifications** writes the new base address of the array indicated by the  _rgntf_ parameter. 
    
 _pcb_
  
> [out] Pointer to the size, in bytes, of the array indicated by the  _pvBaseNew_ parameter. 
    
## Return value

S_OK
  
> A pointer was adjusted successfully.
    
MAPI_E_INVALID_PARAMETER
  
> An invalid notification was encountered.
    
## Remarks

The  _pcb_ parameter to the **ScRelocNotifications** function is optional. 
  
## See also



[ScRelocProps](screlocprops.md)

