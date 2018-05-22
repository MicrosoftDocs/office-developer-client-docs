---
title: "SContentRestriction"
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.SContentRestriction
api_type:
- COM
ms.assetid: 784c8a5a-493e-48e6-8784-ba8122c76e3d
description: "Last modified: March 09, 2015"
---

# SContentRestriction
 
**Applies to**: Outlook 
  
Describes a content restriction, which is used to limit a table view to only those rows that include a column with contents matching a search string. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SContentRestriction
{
  ULONG        ulFuzzyLevel;
  ULONG        ulPropTag;
  LPSPropValue lpProp;
} SContentRestriction;

```

## Members

**ulFuzzyLevel**
  
> Option settings defining the level of preciseness that the content restriction should enforce when you verify for a match.
    
   The **lower 16 bits** of the **ulFuzzyLevel** member apply to properties of type PT_BINARY and PT_STRING8 and must be set to one of the following values: 
    
   - FL_FULLSTRING: To match, the **lpProp** search string must be contained in the property identified by **ulPropTag**.
        
   - FL_PREFIX : To match, the **lpProp** search string must appear at the start of the property identified by **ulPropTag**. The two strings should be compared only up to the length of the search string indicated by **lpProp**. 
        
   - FL_SUBSTRING: To match, the **lpProp** search string must be contained anywhere in the property identified by **ulPropTag**. 
        
   The **upper 16 bits** of the **ulFuzzyLevel** member apply only to properties of type PT_STRING8 and can be set to the following values in any combination: 
        
   - FL_IGNORECASE: The comparison should be made without considering case. 
        
   - FL_IGNORENONSPACE: The comparison should ignore Unicode-defined non-spacing characters such as diacritical marks. 
        
   - FL_LOOSE: The comparison should give you a match whenever possible, ignoring case and non-spacing characters. 
    
**ulPropTag**
  
> Property tag identifying the string property to be checked for occurrence of the search string. 
    
**lpProp**
  
> Pointer to a property value structure that contains the string value to use as the search string.
    
## Remarks

There are two property tags in an **SContentRestriction** structure: one in the **ulPropTag** member and the other in the **ulPropTag** member of the **SPropValue** structure pointed to by **lpProp**. In both tags, MAPI requires only the property type field and ignores the property identifier field. However, the two property types must match, or else the error value MAPI_E_TOO_COMPLEX is returned when the restriction is used in a call to [IMAPITable::Restrict](imapitable-restrict.md) or [IMAPITable::FindRow](imapitable-findrow.md). 
  
The values FL_FULLSTRING, FL_PREFIX, and FL_SUBSTRING are mutually exclusive. Only one of them can be set, and one of them must be set. Their meanings are fixed, and the provider must implement them exactly as defined. The provider should return MAPI_E_TOO_COMPLEX if it is unable to support these values. 
  
The values FL_IGNORECASE, FL_IGNORENONSPACE, and FL_LOOSE are independent. Anywhere from zero to all three of them can be set. Their definitions are provided as a guideline only, and the provider is free to implement its own specific meaning of each flag. The provider should not return any error indication if it has no implementation of a specified flag. 
  
The result of a content restriction imposed against a property is undefined when the property does not exist. When a client requires well-defined behavior for such a restriction and is not sure whether the property exists for example, it is not a required column of a table it should create an **AND** restriction to join the content restriction with an exist restriction. Use an [SExistRestriction](sexistrestriction.md) structure to define the exist restriction and an [SAndRestriction](sandrestriction.md) structure to define the **AND** restriction. 
  
For more information about the **SContentRestriction** structure and restrictions in general, see [About Restrictions](about-restrictions.md).
  
## See also

- [SPropValue](spropvalue.md)
- [SRestriction](srestriction.md)
- [MAPI Structures](mapi-structures.md)

