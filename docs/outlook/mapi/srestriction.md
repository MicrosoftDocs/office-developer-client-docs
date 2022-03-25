---
title: "SRestriction"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SRestriction
api_type:
- COM
ms.assetid: c12b4409-da6f-480b-87af-1e5baea2e8bd
description: "Describes a filter for limiting the view of a table to particular rows for Outlook 2013 and Outlook 2016."
---

# SRestriction

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes a filter for limiting the view of a table to particular rows. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SRestriction
{
  ULONG rt;
  union
  {
    SComparePropsRestriction resCompareProps;
    SAndRestriction resAnd;
    SOrRestriction resOr;
    SNotRestriction resNot;
    SContentRestriction resContent;
    SPropertyRestriction resProperty;
    SBitMaskRestriction resBitMask;
    SSizeRestriction resSize;
    SExistRestriction resExist;
    SSubRestriction resSub;
    SCommentRestriction resComment;
  } res;
} SRestriction;

```

## Members

 **rt**
  
> The restriction type. Possible values are as follows: 
    
RES_AND 
  
> An **AND** restriction, which applies a bitwise **AND** operation to a restriction. 
    
RES_BITMASK 
  
> A bitmask restriction, which applies a bitmask to a property value.
    
RES_COMMENT 
  
> A comment restriction, which associates a comment with a restriction.
    
RES_COMPAREPROPS 
  
> A property comparison restriction, which compares two property values.
    
RES_CONTENT 
  
> A content restriction, which searches a property value for specific content.
    
RES_EXIST 
  
> An exist restriction, which determines whether a property is supported.
    
RES_NOT 
  
> A **NOT** restriction, which applies a logical **NOT** operation to a restriction. 
    
RES_OR 
  
> An **OR** restriction, which applies a logical **OR** operation to a restriction. 
    
RES_PROPERTY 
  
> A property restriction, which determines whether a property value matches a particular value.
    
RES_SIZE 
  
> A size restriction, which determines whether a property value is a particular size.
    
RES_SUBRESTRICTION 
  
> A sub-object restriction, which applies a restriction to a message's attachments or recipients.
    
 **res**
  
> Union of restriction structures describing the filter to be applied. The specific structure included in the **res** member depends on the value of the **rt** member. The mapping between restriction type and structure is listed in the following table. 
    
|Property |Value |
|:-----|:-----|
|**Restriction type** <br/> |**Restriction structure** <br/> |
|RES_AND  <br/> |[SAndRestriction](sandrestriction.md) <br/> |
|RES_BITMASK  <br/> |[SBitMaskRestriction](sbitmaskrestriction.md) <br/> |
|RES_COMMENT  <br/> |[SCommentRestriction](scommentrestriction.md) <br/> |
|RES_COMPAREPROPS  <br/> |[SComparePropsRestriction](scomparepropsrestriction.md) <br/> |
|RES_CONTENT  <br/> |[SContentRestriction](scontentrestriction.md) <br/> |
|RES_EXIST  <br/> |[SExistRestriction](sexistrestriction.md) <br/> |
|RES_NOT  <br/> |[SNotRestriction](snotrestriction.md) <br/> |
|RES_OR  <br/> |[SOrRestriction](sorrestriction.md) <br/> |
|RES_PROPERTY  <br/> |[SPropertyRestriction](spropertyrestriction.md) <br/> |
|RES_SIZE  <br/> |[SSizeRestriction](ssizerestriction.md) <br/> |
|RES_SUBRESTRICTION  <br/> |[SSubRestriction](ssubrestriction.md) <br/> |
   
## Remarks

Clients use an **SRestriction** structure to limit the number and type of rows in their view of a table and to search for specific messages in a folder. To impose the limitation on a table, clients call either [IMAPITable::Restrict](imapitable-restrict.md) or [IMAPITable::FindRow](imapitable-findrow.md). To impose the limitation on a folder, clients call the folder's [IMAPIContainer::SetSearchCriteria](imapicontainer-setsearchcriteria.md) method. 
  
For information about how to use restrictions with tables, see [About Restrictions](about-restrictions.md). 
  
## See also



[SAndRestriction](sandrestriction.md)
  
[SBitMaskRestriction](sbitmaskrestriction.md)
  
[SCommentRestriction](scommentrestriction.md)
  
[SComparePropsRestriction](scomparepropsrestriction.md)
  
[SContentRestriction](scontentrestriction.md)
  
[SExistRestriction](sexistrestriction.md)
  
[SNotRestriction](snotrestriction.md)
  
[SOrRestriction](sorrestriction.md)
  
[SPropertyRestriction](spropertyrestriction.md)
  
[SSizeRestriction](ssizerestriction.md)
  
[SSubRestriction](ssubrestriction.md)


[MAPI Structures](mapi-structures.md)

