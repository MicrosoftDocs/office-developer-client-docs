---
title: "SDateTimeArray"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SDateTimeArray
api_type:
- COM
ms.assetid: 6a0dff65-1055-487c-9d15-4cfe336f2ad7
description: "Contains an array of time values that are used to describe a property of type PT_MV_SYSTIME for Outlook 2013 or Outlook 2016."
---

# SDateTimeArray

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an array of time values that are used to describe a property of type PT_MV_SYSTIME.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
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



[FILETIME](filetime.md)
  
[SPropValue](spropvalue.md)


[MAPI Structures](mapi-structures.md)

