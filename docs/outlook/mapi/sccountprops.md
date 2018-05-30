---
title: "ScCountProps"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.ScCountProps
api_type:
- COM
ms.assetid: 76e4cc52-e1a0-4e0b-a2a6-a17644f6b2e7
description: "Last modified: March 09, 2015"
---

# ScCountProps

  
  
**Applies to**: Outlook 
  
Determines the size, in bytes, of a property value array and validates the memory associated with the array. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
SCODE ScCountProps(
  int cprop,
  LPSPropValue rgprop,
  ULONG FAR * pcb
);
```

## Parameters

 _cprop_
  
> [in] Count of properties in the array indicated by the  _rgprop_ parameter. 
    
 _rgprop_
  
> [in] Pointer to a range in an array of [SPropValue](spropvalue.md) structures that defines the properties whose size is to be determined. This range does not necessarily start at the beginning of the array. 
    
 _pcb_
  
> [out] Optional pointer to the size, in bytes, of the property array.
    
## Return value

S_OK 
  
> The call succeeded and has returned the expected value or values. 
    
MAPI_E_INVALID_PARAMETER 
  
> At least one property in the property value array has an identifier of PROP_ID_NULL or PROP_ID_INVALID, or the property array contains a multivalued property with no property values.
    
## Remarks

If NULL is passed in the  _pcb_ parameter, the **ScCountProps** function validates the array of notifications but no counting is done. If a non-null value is passed in  _pcb_, the **ScCountNotifications** function determines the size of the array and stores the cause  _pcb_. The  _pcb_ parameter must be large enough to contain the entire array. 
  
As it is counting, **ScCountProps** validates the memory associated with the array. **ScCountProps** only works with properties about which MAPI has information. 
  
## See also



[PropCopyMore](propcopymore.md)

