---
title: "SAppTimeArray"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SAppTimeArray
api_type:
- COM
ms.assetid: 5a1ff95a-9862-4165-8a70-bd2eeb7fe683
description: "Last modified: March 09, 2015"
---

# SAppTimeArray

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an array of time values.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SAppTimeArray
{
  ULONG cValues;
  double FAR *lpat;
} SAppTimeArray;

```

## Members

 **cValues**
  
> Count of values in the array pointed to by the **lpat** member. 
    
 **lpat**
  
> Pointer to an array of application time values. 
    
## Remarks

The **SAppTimeArray** structure is used to define properties of type PT_MV_APPTIME. For more information about PT_MV_APPTIME, see [List of Property Types](property-types.md).
  
## See also



[MAPI Structures](mapi-structures.md)

