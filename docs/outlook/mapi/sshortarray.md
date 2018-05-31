---
title: "SShortArray"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SShortArray
api_type:
- COM
ms.assetid: 201ceb76-41bc-4d7b-835d-5196bf3dc234
description: "Last modified: March 09, 2015"
---

# SShortArray

  
  
**Applies to**: Outlook 
  
Contains an array of unsigned integer values that are used to describe a property of type PT_MV_SHORT.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SShortArray
{
  ULONG cValues;
  short int FAR *lpi;
} SShortArray;

```

## Members

 **cValues**
  
> Count of values in the array pointed to by the **lpi** member. 
    
 **lpi**
  
> Pointer to an array of unsigned integer values.
    
## Remarks

For more information about PT_MV_SHORT and other property types, see [Property Types](property-types.md). 
  
## See also



[SPropValue](spropvalue.md)


[MAPI Structures](mapi-structures.md)

