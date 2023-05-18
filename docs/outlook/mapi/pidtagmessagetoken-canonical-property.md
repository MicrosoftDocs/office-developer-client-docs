---
title: "PidTagMessageToken Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagMessageToken
api_type:
- HeaderDef
ms.assetid: fcb93346-db92-44b5-a447-59fd95f98f45
description: "Contains an ASN.1 security token for a message. This property conveys protected security-related information from its originator to its recipient."
---

# PidTagMessageToken Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an ASN.1 security token for a message.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_MESSAGE_TOKEN  <br/> |
|Identifier:  <br/> |0x0C03  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Secure Messaging Properties  <br/> |
   
## Remarks

This property conveys protected security-related information from its originator to its recipient. In conjunction with the **PR_MESSAGE_SECURITY_LABEL** ([PidTagMessageSecurityLabel](pidtagmessagesecuritylabel-canonical-property.md)) property, it guarantees the label's association with the message content. In conjunction with the **PR_CONTENT_INTEGRITY_CHECK** ([PidTagContentIntegrityCheck](pidtagcontentintegritycheck-canonical-property.md)) property, it verifies that the message content is unchanged.
  
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

