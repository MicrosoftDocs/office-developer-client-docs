---
title: "SLPSTRArray"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SLPSTRArray
api_type:
- COM
ms.assetid: 5f570d9b-eb3d-4fc7-bcbe-348a0b8fe9e9
description: "Last modified: March 09, 2015"
---

# SLPSTRArray

  
  
**Applies to**: Outlook 
  
Contains an array of string values that are used to describe a property of type PT_MV_STRING8.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```
typedef struct _SLPSTRArray
{
  ULONG cValues;
  LPSTR FAR *lppszA;
} SLPSTRArray;

```

## Members

 **cValues**
  
> Count of values in the array pointed to by the **lppszA** member. 
    
 **lppszA**
  
> Pointer to an array of null-ended 8-bit character strings.
    
## Remarks

For more information about PT_MV_STRING8, see [List of Property Types](property-types.md).
  
## See also

#### Reference

[SPropValue](spropvalue.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

