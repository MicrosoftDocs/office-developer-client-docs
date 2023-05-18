---
title: "SGuidArray"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SGuidArray
api_type:
- COM
ms.assetid: 2091e5fc-75c8-4ea4-87e9-a9bf508e9c58
description: "Contains an array of GUID structures that are used to describe a property of type PT_MV_CLSID."
---

# SGuidArray

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an array of [GUID](guid.md) structures that are used to describe a property of type PT_MV_CLSID. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
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



[GUID](guid.md)
  
[SPropValue](spropvalue.md)


[MAPI Structures](mapi-structures.md)

