---
title: "PROP_ID"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PROP_ID
api_type:
- COM
ms.assetid: 6ddaced5-49bb-41fe-95da-4e3300883bf7
description: "Last modified: March 09, 2015"
---

# PROP_ID

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Returns the property identifier of a specified property tag.
  
|||
|:-----|:-----|
|Header file:  <br/> |Mapidefs.h  <br/> |
|Related structure:  <br/> |[SPropValue](spropvalue.md) <br/> |
   
```
PROP_ID (ulPropTag)
```

## Parameters

 _ulPropTag_
  
> Property tag that contains the identifier to be returned.
    
## Remarks

Every property tag contains the property type in the low-order word (bits 0 through 15) and the property identifier in the high-order word (bits 16 through 31). The **PROP_ID** macro extracts the property identifier and puts it in bits 0 through 15 of the integer to be returned. The remaining bits of the return value are set to zeros. 
  
The **PROP_ID** macro can be used, for example, to retrieve an identifier to pass to [IMAPIProp::GetNamesFromIDs](imapiprop-getnamesfromids.md). **GetNamesFromIDs** retrieves the property name associated with an identifier for a named property. 
  
## See also

#### Reference

[SPropValue](spropvalue.md)
#### Concepts

[Macros Related to Structures](macros-related-to-structures.md)

