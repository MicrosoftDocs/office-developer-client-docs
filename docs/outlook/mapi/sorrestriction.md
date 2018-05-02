---
title: "SOrRestriction"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SOrRestriction
api_type:
- COM
ms.assetid: 6fee29ce-9a34-4e0c-bb71-03120c3f1117
description: "Last modified: March 09, 2015"
---

# SOrRestriction

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Describes an **OR** restriction which is used to apply a logical **OR** operation to a restriction. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```
typedef struct _SOrRestriction
{
  ULONG cRes;
  LPSRestriction lpRes;
} SOrRestriction;

```

## Members

 **cRes**
  
> Count of structures in the array pointed to by the **lpRes** member. 
    
 **lpRes**
  
> Pointer to the [SRestriction](srestriction.md) structure describing the restriction to be joined using the logical **OR** operation. 
    
## Remarks

For more information about the **SOrRestriction** structure, see [About Restrictions](about-restrictions.md). 
  
## See also

#### Reference

[SRestriction](srestriction.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

