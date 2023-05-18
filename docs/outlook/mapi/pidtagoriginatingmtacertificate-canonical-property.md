---
title: "PidTagOriginatingMtaCertificate Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagOriginatingMtaCertificate
api_type:
- COM
ms.assetid: f6b7ff0c-19a0-4cad-8868-c05397fcebf4
description: "Contains an identifier for the message transfer agent (MTA) that originated the message. This property is available on sent messages in the Sent Items folder."
---

# PidTagOriginatingMtaCertificate Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an identifier for the message transfer agent (MTA) that originated the message.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGINATING_MTA_CERTIFICATE  <br/> |
|Identifier:  <br/> |0x0E25  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Server  <br/> |
   
## Remarks

This property, if set, is available on sent messages in the Sent Items folder.
  
This property corresponds to the X.400 report per-message attribute.
  
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

