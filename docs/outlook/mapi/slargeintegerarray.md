---
title: "SLargeIntegerArray"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SLargeIntegerArray
api_type:
- COM
ms.assetid: 9ec9a674-c1a2-4137-856f-6cabe6f0eb9f
description: "Contains an array of LARGE_INTEGER structures that are used to describe a property of type PT_MV_I8."
---

# SLargeIntegerArray

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an array of [LARGE_INTEGER](https://go.microsoft.com/fwlink/?LinkId=132130) structures that are used to describe a property of type PT_MV_I8. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SLargeIntegerArray
{
  ULONG cValues;
  LARGE_INTEGER FAR *lpli;
} SLargeIntegerArray;

```

## Members

 **cValues**
  
> Count of values in the array pointed to by the **lpli** member. 
    
 **lpli**
  
> Pointer to an array of **LARGE_INTEGER** structures holding the integer values. 
    
## Remarks

For more information about PT_MV_18, see [List of Property Types](property-types.md).
  
## See also



[SPropValue](spropvalue.md)


[MAPI Structures](mapi-structures.md)

