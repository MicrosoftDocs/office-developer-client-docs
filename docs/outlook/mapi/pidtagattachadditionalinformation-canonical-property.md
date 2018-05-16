---
title: "PidTagAttachAdditionalInformation Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagAttachAdditionalInformation
api_type:
- HeaderDef
ms.assetid: 75f092f2-ee3f-45c2-a46f-e1dff2e22b2e
description: "Last modified: March 09, 2015"
---

# PidTagAttachAdditionalInformation Canonical Property

  
  
**Applies to**: Outlook 
  
Provides file type information for a non-Windows attachment.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ATTACH_ADDITIONAL_INFO  <br/> |
|Identifier:  <br/> |0x370F  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Message attachment  <br/> |
   
## Remarks

This property provides metadata about a particular attachment based on the attachment's encoding. For example, when the **PR_ATTACH_ENCODING** ( [PidTagAttachEncoding](pidtagattachencoding-canonical-property.md)) property contains MacBinary, **PR_ATTACH_ADDITIONAL_INFO** contains a string that represents the Macintosh file creator and file type, formatted as ":CREA:TYPE" for the encoded Macintosh file. 
  
## Related Resources

### Protocol Specifications

[[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
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

