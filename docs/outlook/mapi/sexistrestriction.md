---
title: "SExistRestriction"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SExistRestriction
api_type:
- COM
ms.assetid: 48d5ab42-ee70-4f6e-9184-18d22b08ea1b
description: "Last modified: March 09, 2015"
---

# SExistRestriction

  
  
**Applies to**: Outlook 
  
Describes an exist restriction which is used to test whether a particular property exists as a column in the table. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SExistRestriction
{
  ULONG ulReserved1;
  ULONG ulPropTag;
  ULONG ulReserved2;
} SExistRestriction;

```

## Members

 **ulReserved1**
  
> Reserved; must be zero. 
    
 **ulPropTag**
  
> Property tag identifying the column to be tested for existence in each row.
    
 **ulReserved2**
  
> Reserved; must be zero.
    
## Remarks

The exist restriction is used to guarantee meaningful results for other types of restrictions that involve properties, such as property and content restrictions. When a restriction that involves a property is passed to [IMAPITable::Restrict](imapitable-restrict.md) or [IMAPITable::FindRow](imapitable-findrow.md) and the property does not exist, the results of the restriction are undefined. By creating an **AND** restriction that joins the property restriction with an exist restriction, a caller can be guaranteed accurate results. 
  
Exist restrictions cannot be used with sub-object properties that have type PT_OBJECT. 
  
For more information about the **SExistRestriction** structure, see [About Restrictions](about-restrictions.md). 
  
## See also



[SRestriction](srestriction.md)


[MAPI Structures](mapi-structures.md)

