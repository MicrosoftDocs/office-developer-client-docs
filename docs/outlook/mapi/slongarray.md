---
title: "SLongArray"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SLongArray
api_type:
- COM
ms.assetid: 57435634-202d-4998-9931-4562f1a66f5f
description: "Last modified: March 09, 2015"
---

# SLongArray

  
  
**Applies to**: Outlook 
  
Contains an array of LONG value types that are used to describe a property of type PT_MV_LONG. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SLongArray
{
  ULONG cValues;
  LONG FAR *lpl;
} SLongArray;

```

## Members

 **cValues**
  
> Count of values in the array pointed to by the **lpl** member. 
    
 **lpl**
  
> Pointer to an array of LONG values.
    
## Remarks

For more information about PT_MV_LONG, see [List of Property Types](property-types.md).
  
## See also



[SPropValue](spropvalue.md)


[MAPI Structures](mapi-structures.md)

