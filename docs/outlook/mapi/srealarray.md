---
title: "SRealArray"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SRealArray
api_type:
- COM
ms.assetid: 95be07bf-5732-4775-9e0f-fec47e99d9b7
description: "Last modified: March 09, 2015"
---

# SRealArray

  
  
**Applies to**: Outlook 
  
Contains an array of float values that are used to describe a property of type PT_MV_R4. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SRealArray
{
  ULONG cValues;
  float FAR *lpflt;
} SRealArray;

```

## Members

 **cValues**
  
> Count of values in the array pointed to by the **lpflt** member. 
    
 **lpflt**
  
> Pointer to an array of float values.
    
## Remarks

For more information about the PT_MV_R4 property type, see [Property Types](property-types.md).
  
## See also



[SPropValue](spropvalue.md)


[MAPI Structures](mapi-structures.md)

