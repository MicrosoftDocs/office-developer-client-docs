---
title: "PidTagAttachMimeSequence Canonical Property"
description: Outlines the PidTagAttachMimeSequence canonical property, which contains the MIME sequence number of a MIME message attachment.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagAttachMimeSequence
api_type:
- HeaderDef
ms.assetid: d2a84f24-b4a5-4e16-9219-7a579a31a8f8
---

# PidTagAttachMimeSequence Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the MIME sequence number of a MIME message attachment.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_ATTACH_MIME_SEQUENCE  <br/> |
|Identifier:  <br/> |0x3710  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Message Attachment Properties  <br/> |
   
## Remarks

This property is used for MHTML support. It represents the sequence number of the attachment within the parent MIME multipart body part of the MIME message.
  
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

