---
title: "SSizeRestriction"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SSizeRestriction
api_type:
- COM
ms.assetid: 4e7340d1-3cb9-4276-b83f-1c8f94acb909
description: "Last modified: March 09, 2015"
---

# SSizeRestriction

  
  
**Applies to**: Outlook 
  
Describes a size restriction which is used to test the size of a property value. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SSizeRestriction
{
  ULONG relop;
  ULONG ulPropTag;
  ULONG cb;
} SSizeRestriction;

```

## Members

 **relop**
  
> Relational operator that is used in the size comparison. Possible values are as follows: 
    
RELOP_GE 
  
> The comparison is made based on a greater or equal first value.
    
RELOP_GT 
  
> The comparison is made based on a greater first value.
    
RELOP_LE 
  
> The comparison is made based on a lesser or equal first value.
    
RELOP_LT 
  
> The comparison is made based on a lesser first value.
    
RELOP_NE 
  
> The comparison is made based on unequal values.
    
RELOP_RE 
  
> The comparison is made based on LIKE (regular expression) values.
    
RELOP_EQ 
  
> The comparison is made based on equal values.
    
 **ulPropTag**
  
> Property tag identifying the property to test.
    
 **cb**
  
> Count of bytes in the property value.
    
## Remarks

For a general discussion of how restrictions work, see [About Restrictions](about-restrictions.md). 
  
## See also

#### Reference

[SRestriction](srestriction.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

