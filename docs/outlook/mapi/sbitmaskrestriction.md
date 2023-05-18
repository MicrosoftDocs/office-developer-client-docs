---
title: "SBitMaskRestriction"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SBitMaskRestriction
api_type:
- COM
ms.assetid: ddd42180-6e4f-410c-9f78-d868a91452dc
description: "Describes a bitmask restriction, which is used to perform a bitwise AND operation and test the result."
---

# SBitMaskRestriction

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Describes a bitmask restriction, which is used to perform a bitwise **AND** operation and test the result. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
   
```cpp
typedef struct _SBitMaskRestriction
{
  ULONG relBMR;
  PT_LONG ulPropTag;
  ULONG ulMask;
} SBitMaskRestriction;

```

## Members

 **relBMR**
  
> Relational operator that describes how the mask specified in the **ulMask** member should be applied to the property tag. Possible values are as follows: 
    
BMR_EQZ 
  
> Perform a bitwise **AND** operation of the mask in the **ulMask** member with the property represented by the **ulPropTag** member and test for being equal to zero. 
    
BMR_NEZ 
  
> Perform a bitwise **AND** operation of the mask in the **ulMask** member with the property represented by the **ulPropTag** member and test for being not equal to zero. 
    
 **ulPropTag**
  
> Property tag of the property to which the bitmask is applied.
    
 **ulMask**
  
> Bitmask to apply to the property identified by **ulPropTag**.
    
## Remarks

The **SBitMaskRestriction** structure performs a bitwise **AND** operation using the bitmask described in the **ulMask** member and the value of the property described by the **ulPropTag** member. If the result is zero, BMR_EQZ is satisfied. If it is nonzero, that is, if the property value has at least one of the same bits set as **ulMask**, then BMR_NEZ is satisfied.
  
For more information about the **SBitMaskRestriction** structure and restrictions in general, see [About Restrictions](about-restrictions.md).
  
## See also



[SRestriction](srestriction.md)


[MAPI Structures](mapi-structures.md)

