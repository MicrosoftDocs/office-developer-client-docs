---
title: "PidNameCrossReference Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidNameCrossReference
api_type:
- COM
ms.assetid: d16e1adf-c911-427e-9c98-678a303e6791
description: "Last modified: March 09, 2015"
---

# PidNameCrossReference Canonical Property

  
  
**Applies to**: Outlook 
  
Contains an [RFC3282] Xref header field value.
  
|||
|:-----|:-----|
|Friendly names:  <br/> |None  <br/> |
|Property set:  <br/> |PS_INTERNET_HEADERS  <br/> |
|Property name:  <br/> |Xref  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |E-mail  <br/> |
   
## Remarks

To set the value of this property, Multipurpose Internet Message Extensions (MIME) clients must write the desired value to an XRef header field. MIME readers must copy the value of an XRef header field to the value of this property.
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXCMAIL]](http://msdn.microsoft.com/library/b60d48db-183f-4bf5-a908-f584e62cb2d4%28Office.15%29.aspx)
  
> Converts from Internet standard e-mail conventions to message objects.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

