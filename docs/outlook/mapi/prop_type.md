---
title: "PROP_TYPE"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PROP_TYPE
api_type:
- COM
ms.assetid: 746d63fa-bfb7-479f-94dc-ba40011c1ec9
description: "Last modified: March 09, 2015"
---

# PROP_TYPE

  
  
**Applies to**: Outlook 
  
Returns the property type of a specified property tag.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |[SPropValue](spropvalue.md) <br/> |
   
```
PROP_TYPE (ulPropTag)
```

## Parameters

 _ulPropTag_
  
> Property tag that contains the property type to be returned.
    
## Remarks

The **PROP_TYPE** macro can be used to determine the type of a property. For example, calling PROP_TYPE ( **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md))) results in the value PT_BINARY being returned.
  
Every property tag contains the property type in the low-order word (bits 0 through 15) and the property identifier in the high-order word (bits 16 through 31). The **PROP_TYPE** macro extracts the property type and puts it in bits 0 through 15 of the integer to be returned. The remaining bits of the return value are set to zeros. 
  
## See also

#### Reference

[SPropValue](spropvalue.md)
#### Concepts

[Macros Related to Structures](macros-related-to-structures.md)

