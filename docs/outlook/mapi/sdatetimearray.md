---
title: "SDateTimeArray"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SDateTimeArray
api_type:
- COM
ms.assetid: 6a0dff65-1055-487c-9d15-4cfe336f2ad7
description: "Last modified: March 09, 2015"
---

# SDateTimeArray

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Contains an array of time values that are used to describe a property of type PT_MV_SYSTIME.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```
typedef struct _SDateTimeArray
{
  ULONG cValues;
  FILETIME FAR *lpft;
} SDateTimeArray;

```

## Members

 **cValues**
  
> Count of values in the array pointed to by the **lpft** member. 
    
 **lpft**
  
> Pointer to an array of [FILETIME](filetime.md) structures that contain the time values. 
    
## Remarks

For more information about PT_MV_SYSTIME, see [List of Property Types](property-types.md).
  
## See also

#### Reference

[FILETIME](filetime.md)
  
[SPropValue](spropvalue.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

