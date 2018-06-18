---
title: "FPropContainsProp"
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.FPropContainsProp
api_type:
- COM
ms.assetid: 43da5b59-7691-49aa-b83c-753d43bfd8fd
description: "Last modified: March 09, 2015"
---

# FPropContainsProp

**Applies to**: Outlook 2013 | Outlook 2016 
  
Compares two property values, generally strings or binary arrays, to see if one contains the other. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapiutil.h  <br/> |
|Implemented by:  <br/> |MAPI  <br/> |
|Called by:  <br/> |Client applications and service providers  <br/> |
   
```cpp
BOOL FPropContainsProp(
  LPSPropValue lpSPropValueDst,
  LPSPropValue lpSPropValueSrc,
  ULONG ulFuzzyLevel
);
```

## Parameters

_lpSPropValueDst_
  
> [in] Pointer to an [SPropValue](spropvalue.md) structure defining the property value that might contain the search string pointed to by the  _lpSPropValueSrc_ parameter. 
    
_lpSPropValueSrc_
  
> [in] Pointer to an **SPropValue** structure defining the search string that **FPropContainsProp** is seeking in the property value pointed to by the  _lpSPropValueDst_ parameter. 
    
_ulFuzzyLevel_
  
> [in] Option settings defining the level of preciseness to use in the comparison. 

  - The **lower 16 bits** apply to properties of type PT_BINARY and PT_STRING8. They must be set to exactly one of the following values:
      
    - FL_FULLSTRING: The  _lpSPropValueSrc_ search string must be equal to the property value identified by  _lpSPropValueDst_.
        
    - FL_PREFIX: The  _lpSPropValueSrc_ search string must appear at the beginning of the property value identified by  _lpSPropValueDst_. The two values should be compared only up to the length of the search string indicated by  _lpSPropValueSrc_. 
        
    - FL_SUBSTRING: The  _lpSPropValueSrc_ search string must be contained anywhere in the property value identified by  _lpSPropValueDst_. 
      
  - The **upper 16 bits** apply only to properties of type PT_STRING8. They can be set to the following values in any combination:
    
    - FL_IGNORECASE: The comparison should be made without considering case sensitivity. 
        
    - FL_IGNORENONSPACE: The comparison should ignore Unicode-defined nonspacing characters such as diacritical marks. 
        
    - FL_LOOSE: The comparison should indicate a match whenever possible, ignoring case sensitivity and nonspacing characters.
    
## Return value

TRUE 
  
> The parameters are all valid and the  _lpSPropValueSrc_ search string is contained as specified in the  _lpSPropValueDst_ property value. 
    
FALSE 
  
> The property values being compared are not of type PT_STRING8 or PT_BINARY, the property values are of different types, or the  _lpSPropValueSrc_ search string is not contained as specified in the  _lpSPropValueDst_ property value. 
    
## Remarks

The comparison method depends on the property types specified in the [SPropValue](spropvalue.md) property definitions and the fuzzy level heuristic provided in the  _ulFuzzyLevel_ parameter. The [FPropCompareProp](fpropcompareprop.md) and **FPropContainsProp** functions can be used to prepare restrictions for generating a table. 
  
The upper 16 bits of  _ulFuzzyLevel_ are ignored for property type PT_BINARY. If the settings in  _ulFuzzyLevel_ are missing or invalid, a full-string exact match is performed. For more information about property containment, see the [SContentRestriction](scontentrestriction.md) structure. 
  

