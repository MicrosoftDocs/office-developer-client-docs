---
title: "PidTagTextAttachmentCharset Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagTextAttachmentCharset
api_type:
- COM
ms.assetid: d347c949-d0c3-4a36-8447-3fa01111cdc1
description: "Contains a message attachment's character set value. This property's data is derived from a Content-Type MIME header field that starts with 'text/'."
---

# PidTagTextAttachmentCharset Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a message attachment's character set value.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |None  <br/> |
|Identifier:  <br/> |0x371B  <br/> |
|Data type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |Message attachment  <br/> |
   
## Remarks

This property's data is derived from a Content-Type MIME header field that starts with "text/", if a "charset" parameter is present.
  
## Related resources

### Protocol specifications

[[MS-OXCMAIL]](https://msdn.microsoft.com/library/b60d48db-183f-4bf5-a908-f584e62cb2d4%28Office.15%29.aspx)
  
> Converts from Internet standard email conventions to message objects.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

