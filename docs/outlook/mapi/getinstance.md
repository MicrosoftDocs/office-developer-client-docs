---
title: "GetInstance"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.GetInstance
api_type:
- COM
ms.assetid: cb432d52-6c96-45d2-bbde-45b0de3f915c
description: "Last modified: March 09, 2015"
---

# GetInstance

  
  
**Applies to**: Outlook 
  
Copies one value within a multivalued property to a single-valued property of the same type. 
  
|||
|:-----|:-----|
|Header file:  <br/> |MAPIUTIL.H  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
VOID GetInstance(
  LPSPropValue pvalMv,
  LPSPropValue pvalSv,
  ULONG uliInst
);
```

## Parameters

 _pvalMv_
  
> [in] Pointer to an [SPropValue](spropvalue.md) structure defining a multivalued property. 
    
 _pvalSv_
  
> [in] Pointer to a single-valued property to receive data. 
    
 _uliInst_
  
> [in] The instance number, that is, the array element, of the value being copied from the structure indicated by the  _pvalMv_ parameter. 
    
## Return value

None.
  
## Remarks

If the value copied is too large for the allocated memory, the **GetInstance** function only copies pointers instead of allocating new memory. 
  

