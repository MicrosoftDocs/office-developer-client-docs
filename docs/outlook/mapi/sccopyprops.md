---
title: "ScCopyProps"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.ScCopyProps
api_type:
- COM
ms.assetid: 08bc256c-9706-4f3e-9a12-3e9cca5e4caa
description: "Last modified: March 09, 2015"
---

# ScCopyProps

  
  
**Applies to**: Outlook 
  
Copies the properties defined by an array of [SPropValue](spropvalue.md) structures to a new destination. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
SCODE ScCopyProps(
  int cprop,
  LPSPropValue rgprop,
  LPVOID pvDst,
  ULONG FAR * pcb
);
```

## Parameters

 _cprop_
  
> [in] Count of properties to be copied. 
    
 _rgprop_
  
> [in] Pointer to an array of [SPropValue](spropvalue.md) structures that define the properties to be copied. The  _rgprop_ parameter does not have to point to the beginning of the array, but it must point to the beginning of one of the **SPropValue** structures in the array. 
    
 _pvDst_
  
> [in] Pointer to the initial position in memory to which this function copies the properties. 
    
 _pcb_
  
> [out] Optional pointer to the size, in bytes, of the block of memory pointed to by the  _pvDst_ parameter. 
    
## Return value

S_OK
  
> Properties were copied successfully.
    
MAPI_E_INVALID_PARAMETER
  
> An unknown property type was encountered.
    
## Remarks

The new array and its data reside in a buffer created with a single allocation, and the [ScRelocProps](screlocprops.md) function can be used to adjust the pointers in the individual [SPropValue](spropvalue.md) structures. Prior to this adjustment, the pointers are valid. 
  
 **ScCopyProps** maintains the original property order for the copied property array. 
  
The  _pcb_ parameter is optional; if it is not NULL, it is set to the number of bytes stored in the  _pvDst_ parameter. 
  
## See also

#### Reference

[ScDupPropset](scduppropset.md)

