---
title: "PidTagContentIntegrityCheck Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagContentIntegrityCheck
api_type:
- HeaderDef
ms.assetid: c7f10b8a-6b20-44cf-bde6-8d2b711c1c14
description: "Last modified: March 09, 2015"
---

# PidTagContentIntegrityCheck Canonical Property

  
  
**Applies to**: Outlook 
  
Contains an ASN.1 content integrity check value that allows a message sender to protect message content from disclosure to unauthorized recipients.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_CONTENT_INTEGRITY_CHECK  <br/> |
|Identifier:  <br/> |0x0C00  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Exchange  <br/> |
   
## Remarks

This property provides for non-repudiation of message content. In conjunction with **PR_MESSAGE_TOKEN** ([PidTagMessageToken](pidtagmessagetoken-canonical-property.md)), it ensures that the content of a message arrives at its destination unchanged.
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

