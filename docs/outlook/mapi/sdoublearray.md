---
title: "SDoubleArray"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SDoubleArray
api_type:
- COM
ms.assetid: b63b26de-faf9-453c-ab8b-fb703ed09ae8
description: "Last modified: March 09, 2015"
---

# SDoubleArray

  
  
**Applies to**: Outlook 
  
Contains an array of doubles used to describe a property of type PT_MV_DOUBLE.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SDoubleArray
{
  ULONG cValues;
  double FAR *lpdbl;
} SDoubleArray;

```

## Members

 **cValues**
  
> Count of values in the array pointed to by the **lpdbl** member. 
    
 **lpdbl**
  
> Pointer to an array of double values.
    
## Remarks

For more information about PT_MV_DOUBLE, see [List of Property Types](property-types.md).
  
## See also

#### Reference

[SPropValue](spropvalue.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

