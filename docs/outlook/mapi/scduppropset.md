---
title: "ScDupPropset"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.ScDupPropset
api_type:
- COM
ms.assetid: 165ffbd0-54aa-4692-8bd1-09e6ff3762df
description: "Last modified: March 09, 2015"
---

# ScDupPropset

  
  
**Applies to**: Outlook 
  
Duplicates a property value array in a single block of MAPI memory combining the operations of the [ScCopyProps](sccopyprops.md) and [ScCountProps](sccountprops.md) functions. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```
SCODE ScDupPropset(
  int cprop,
  LPSPropValue rgprop,
  LPALLOCATEBUFFER lpAllocateBuffer,
  LPSPropValue FAR * prgprop
);
```

## Parameters

 _cprop_
  
> [in] Count of property values in the array indicated by the  _rgprop_ parameter. 
    
 _rgprop_
  
> [in] Pointer to an array of [SPropValue](spropvalue.md) structures defining the property values to be duplicated. 
    
 _lpAllocateBuffer_
  
> [in] Pointer to the [MAPIAllocateBuffer](mapiallocatebuffer.md) function, to be used to allocate memory for the duplicated array. 
    
 _prgprop_
  
> [out] Pointer to the initial position in memory where the returned duplicated array of **SPropValue** structures is stored. 
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values.
    

