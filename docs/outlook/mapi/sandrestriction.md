---
title: "SAndRestriction"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SAndRestriction
api_type:
- COM
ms.assetid: 1b7dfe87-f87f-43e3-8332-a0d9c3f70d16
description: "Last modified: March 09, 2015"
---

# SAndRestriction

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes an **AND** restriction, which is used to join a group of restrictions using a logical **AND** operation. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SAndRestriction
{
  ULONG cRes;
  LPSRestriction lpRes;
} SAndRestriction;

```

## Members

 **cRes**
  
> Count of search restrictions in the array pointed to by the **lpRes** member. 
    
 **lpRes**
  
> Pointer to an array of [SRestriction](srestriction.md) structures that will be combined with a logical **AND** operation. 
    
## Remarks

The result of the **SAndRestriction** is TRUE if all its child restrictions evaluate to TRUE. It is FALSE if any child restriction evaluates to FALSE. 
  
For a description of types of restrictions, how to build them, and sample code, see [About Restrictions](about-restrictions.md).
  
## See also



[SRestriction](srestriction.md)


[MAPI Structures](mapi-structures.md)

