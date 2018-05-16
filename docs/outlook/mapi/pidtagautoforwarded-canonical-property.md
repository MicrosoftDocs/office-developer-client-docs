---
title: "PidTagAutoForwarded Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagAutoForwarded
api_type:
- HeaderDef
ms.assetid: 1ba40cc2-ba27-4d75-9682-c536cf3a0d58
description: "Last modified: March 09, 2015"
---

# PidTagAutoForwarded Canonical Property

  
  
**Applies to**: Outlook 
  
Contains TRUE if the client requests an X-MS-Exchange-Organization-AutoForwarded header field.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_AUTO_FORWARDED  <br/> |
|Identifier:  <br/> |0x0005  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |General reporting  <br/> |
   
## Remarks

If this property is set to FALSE or not used, no X-MS-Exchange-Organization-AutoForwarded header field will be created.
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Defines each property that is used in the objects that are described by MS-OXO-prefixed documents.
    
[[MS-OXCMAIL]](http://msdn.microsoft.com/library/b60d48db-183f-4bf5-a908-f584e62cb2d4%28Office.15%29.aspx)
  
> Converts from Internet standard e-mail conventions to message objects.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

