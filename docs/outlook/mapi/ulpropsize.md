---
title: "UlPropSize"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.UlPropSize
api_type:
- COM
ms.assetid: 240f1144-0805-4cd1-9e7d-f2a550a2f160
description: "Last modified: March 09, 2015"
---

# UlPropSize

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns the size of a single property value. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
ULONG UlPropSize(
  LPSPropValue lpSPropValue
);
```

## Parameters

 _lpSPropValue_
  
> [in] Pointer to an [SPropValue](spropvalue.md) structure defining the property to be measured. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values. 
    
MAPI_E_CALL_FAILED 
  
> An error of unexpected or unknown origin prevented the operation from completing.
    
## Remarks

The **UlPropSize** function returns the size, in bytes, of the property value for the specified property. It disregards the size of the remainder of the **SPropValue** structure. 
  

