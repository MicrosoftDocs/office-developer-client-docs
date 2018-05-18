---
title: "SNotRestriction"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SNotRestriction
api_type:
- COM
ms.assetid: e86ca032-d973-4b79-976e-5240ab38a0da
description: "Last modified: March 09, 2015"
---

# SNotRestriction

  
  
**Applies to**: Outlook 
  
Describes a **NOT** restriction, which is used to apply a logical **NOT** operation to a restriction. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SNotRestriction
{
  ULONG ulReserved;
  LPSRestriction lpRes;
} SNotRestriction;

```

## Members

 **ulReserved**
  
> [in] Reserved; must be zero.
    
 **lpRes**
  
> Pointer to a [SRestriction](srestriction.md) structure describing the restriction to be joined to the logical **NOT** operator. 
    
## Remarks

For more information about the **SNotRestriction** structure, see [About Restrictions](about-restrictions.md). 
  
## See also



[SRestriction](srestriction.md)


[MAPI Structures](mapi-structures.md)

