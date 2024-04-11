---
title: "SCommentRestriction"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SCommentRestriction
api_type:
- COM
ms.assetid: 07631ae1-981e-4c8e-a30b-1213904fe079
description: "Describes a comment restriction, which is used to annotate a restriction. Comment restrictions are unlike other restrictions because they are not evaluated."
---

# SCommentRestriction

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes a comment restriction, which is used to annotate a restriction. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
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



[SPropValue](spropvalue.md)
  
[SRestriction](srestriction.md)
  
[SPropertyRestriction](spropertyrestriction.md)


[MAPI Structures](mapi-structures.md)

