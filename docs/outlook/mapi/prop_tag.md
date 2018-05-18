---
title: "PROP_TAG"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PROP_TAG
api_type:
- COM
ms.assetid: d8c9d18c-4043-41f3-8501-8be8e3a2c9ac
description: "Last modified: March 09, 2015"
---

# PROP_TAG

  
  
**Applies to**: Outlook 
  
Returns a property tag created by combining a specified property type and identifier. 
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |[SPropValue](spropvalue.md) <br/> |
   
```cpp
PROP_TAG (ulPropType, ulPropID)
```

## Parameters

 _ulPropType_
  
> Property type for the new property tag.
    
 _ulPropID_
  
> Property identifier for the new property tag.
    
## Remarks

The **PROP_TAG** macro creates a property tag for a property of type  _ulPropType_ and the identifier that is specified in  _ulPropID_. For example, a property tag for an entry identifier can be created by using the **PROP_TAG** macro as follows: 
  
```
PROP_TAG( PT_BINARY, 0x0FFF)

```

The low-order 16 bits of the returned property tag contain the property type, PT_BINARY, and the high-order 16 bits contain the property identifier, 0xFFFF.
  
For more information about property tags, see [MAPI Property Tags](mapi-property-tags.md).
  
## See also

#### Reference

[SPropValue](spropvalue.md)
#### Concepts

[Macros Related to Structures](macros-related-to-structures.md)

