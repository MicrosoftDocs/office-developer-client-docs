---
title: "PROP_TYPE"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PROP_TYPE
api_type:
- COM
ms.assetid: 746d63fa-bfb7-479f-94dc-ba40011c1ec9
description: "Returns the property type of a specified property tag for Outlook 2013 and Outlook 2016."
---

# PROP_TYPE

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Returns the property type of a specified property tag.
  
|Property |Value |
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |[SPropValue](spropvalue.md) <br/> |
   
```cpp
PROP_TYPE (ulPropTag)
```

## Parameters

 _ulPropTag_
  
> Property tag that contains the property type to be returned.
    
## Remarks

The **PROP_TYPE** macro can be used to determine the type of a property. For example, calling PROP_TYPE (**PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md))) results in the value PT_BINARY being returned.
  
Every property tag contains the property type in the low-order word (bits 0 through 15) and the property identifier in the high-order word (bits 16 through 31). The **PROP_TYPE** macro extracts the property type and puts it in bits 0 through 15 of the integer to be returned. The remaining bits of the return value are set to zeros. 
  
## See also



[SPropValue](spropvalue.md)


[Macros Related to Structures](macros-related-to-structures.md)

