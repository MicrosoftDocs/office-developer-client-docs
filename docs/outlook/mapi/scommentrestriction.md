---
title: "SCommentRestriction"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SCommentRestriction
api_type:
- COM
ms.assetid: 07631ae1-981e-4c8e-a30b-1213904fe079
description: "Last modified: March 09, 2015"
---

# SCommentRestriction

  
  
**Applies to**: Outlook 
  
Describes a comment restriction, which is used to annotate a restriction. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```
typedef struct _SCommentRestriction
{
  ULONG          cValues;
  LPSRestriction lpRes;
  LPSPropValue   lpProp;
} SCommentRestriction;

```

## Members

 **cValues**
  
> Count of property values in the array pointed to by the **lpProp** member. 
    
 **lpRes**
  
> Pointer to an [SRestriction](srestriction.md) structure. 
    
 **lpProp**
  
> Pointer to an array of [SPropValue](spropvalue.md) structures, each containing the property tag and value for a named property. 
    
## Remarks

The **SCommentRestriction** structure associates an object together with a set of named properties. Comment restrictions are unlike other restrictions because they are not evaluated. That is, they are ignored by the [IMAPITable::Restrict](imapitable-restrict.md) method. There is no effect on the rows returned by the [IMAPITable::QueryRows](imapitable-queryrows.md) method after an **IMAPITable::Restrict** call has been made. 
  
The **SCommentRestriction** structure can be used to keep application-specific information with a restriction when it is saved on disk. For example, a client saving the name of a named property used in a property restriction can do so in an **SCommentRestriction** structure. Saving a property name is not possible in a property restriction because the associated [SPropertyRestriction](spropertyrestriction.md) structure holds only the property tag. 
  
For more information about the **SCommentRestriction** structure and restrictions in general, see [About Restrictions](about-restrictions.md). 
  
## See also

#### Reference

[SPropValue](spropvalue.md)
  
[SRestriction](srestriction.md)
  
[SPropertyRestriction](spropertyrestriction.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

