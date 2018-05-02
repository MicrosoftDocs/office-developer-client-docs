---
title: "SComparePropsRestriction"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SComparePropsRestriction
api_type:
- COM
ms.assetid: 3231a91a-1ef2-4dd8-9f3e-79ca56d2eae9
description: "Last modified: March 09, 2015"
---

# SComparePropsRestriction

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Describes a compare property restriction, which tests two properties using a relational operator. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```
typedef struct _SComparePropsRestriction
{
  ULONG relop;
  ULONG ulPropTag1;
  ULONG ulPropTag2;
} SComparePropsRestriction;

```

## Members

 **relop**
  
> Relational operator to use to compare the two properties. Possible values are as follows:
    
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
    
 **ulPropTag1**
  
> Property tag of the first property to be compared. 
    
 **ulPropTag2**
  
> Property tag of the second property to be compared.
    
## Remarks

The comparison order is  _(property tag 1) (relational operator) (property tag 2)_. The properties to be compared must be of the same type. Attempting to compare properties of different types causes MAPI or the service provider to return the error value MAPI_E_TOO_COMPLEX from the [IMAPITable](imapitableiunknown.md) method to which the structure is passed as a parameter. 
  
The result of a compare property value restriction is undefined when one or both of the properties do not exist. When a client requires well-defined behavior for such a restriction and is not sure whether the property exists, (for example, it is not a required column of a table) it should create an **AND** restriction to join the compare property restriction with an exist restriction. Use an [SExistRestriction](sexistrestriction.md) structure to define the exist restriction and an [SAndRestriction](sandrestriction.md) structure to define the **AND** restriction. 
  
The properties specified in the **ulPropTag1** and **ulPropTag2** members can be multi-valued if the service provider supports it. 
  
For more information about the **SComparePropsRestriction** structure and restrictions in general, see [About Restrictions](about-restrictions.md).
  
## See also

#### Reference

[SBitMaskRestriction](sbitmaskrestriction.md)
  
[SRestriction](srestriction.md)
#### Concepts

[MAPI Structures](mapi-structures.md)

