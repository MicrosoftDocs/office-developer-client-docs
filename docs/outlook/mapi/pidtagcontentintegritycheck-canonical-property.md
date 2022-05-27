---
title: "PidTagContentIntegrityCheck Canonical Property"
description: Outlines the PidTagContentIntegrityCheck canonical property, which provides for non-repudiation of message content.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagContentIntegrityCheck
api_type:
- HeaderDef
ms.assetid: c7f10b8a-6b20-44cf-bde6-8d2b711c1c14
---

# PidTagContentIntegrityCheck Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an ASN.1 content integrity check value that allows a message sender to protect message content from disclosure to unauthorized recipients.
  
|Property|Value|
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

