---
title: "SPropTagArray"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.SPropTagArray
api_type:
- COM
ms.assetid: 4a9e1579-bebe-4a51-8ced-6dba9c3bcb63
description: "Contains an array of property tags. A property tag is a 32-bit unsigned integer that consists of two parts."
---

# SPropTagArray

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an array of property tags. 
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related macros:  <br/> |[CbNewSPropTagArray](cbnewsproptagarray.md), [CbSPropTagArray](cbsproptagarray.md), [SizedSPropTagArray](sizedsproptagarray.md) <br/> |
   
```cpp
typedef struct _SPropTagArray
{
  ULONG cValues;
  ULONG aulPropTag[MAPI_DIM];
} SPropTagArray, FAR *LPSPropTagArray;

```

## Members

 **cValues**
  
> Count of property tags in the array indicated by the **aulPropTag** member. 
    
 **aulPropTag**
  
> Array of property tags.
    
## Remarks

A property tag is a 32-bit unsigned integer that consists of two parts: 
  
- An identifier in the high-order 16 bits.
    
- A type in the low-order 16 bits.
    
The identifier is a numeric value in a particular range. MAPI defines ranges for identifiers to describe what the property is used for and who is responsible for maintaining it. MAPI defines constraints for each of the property tags that it supports in the Mapitags.h header file.
  
The type indicates the format for the property's value. MAPI defines constants for each of the property types that it supports in the Mapidefs.h header file. 
  
For more information about property tags and their components, see one of the following topics: 
  
[MAPI Property Tags](mapi-property-tags.md)
  
[MAPI Property Identifier Overview](mapi-property-identifier-overview.md)
  
[MAPI Property Type Overview](mapi-property-type-overview.md)
  
For a complete list of the single-valued and multi-valued property types, see the appendix, [Property Identifiers and Types](property-identifiers-and-types.md). 
  
## See also



[MAPI Structures](mapi-structures.md)

