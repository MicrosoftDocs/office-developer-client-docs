---
title: "SGuidArray"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SGuidArray
api_type:
- COM
ms.assetid: 2091e5fc-75c8-4ea4-87e9-a9bf508e9c58
description: "Last modified: March 09, 2015"
---

# SGuidArray

  
  
**Applies to**: Outlook 
  
Contains an array of [GUID](guid.md) structures that are used to describe a property of type PT_MV_CLSID. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```
typedef struct _SGuidArray
{
  ULONG cValues;
  GUID FAR *lpguid;
} SGuidArray;

```

## Members

 **cValues**
  
> Count of values in the array pointed to by the **lpguid** member. 
    
 **lpguid**
  
> Pointer to an array of **GUID** structures that contains the class identifier values. 
    
## Remarks

For more information about PT_MV_CLSID, see [List of Property Types](property-types.md).
  
## See also

#### Reference

[GUID](guid.md)
  
[SPropValue](spropvalue.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

