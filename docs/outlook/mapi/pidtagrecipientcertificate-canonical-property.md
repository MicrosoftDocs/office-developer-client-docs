---
title: "PidTagRecipientCertificate Canonical Property"
description: Outlines the PidTagRecipientCertificate canonical property, which contains a message recipient's ASN.1 certificate for use in a report.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagRecipientCertificate
api_type:
- COM
ms.assetid: 7c5c749e-5463-4935-85b5-32219d06f782
---

# PidTagRecipientCertificate Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a message recipient's ASN.1 certificate for use in a report.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_RECIPIENT_CERTIFICATE  <br/> |
|Identifier:  <br/> |0x0C13  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI Recipient  <br/> |
   
## Remarks

This property is a copy of the recipient's **PR_USER_CERTIFICATE** ([PidTagUserCertificate](pidtagusercertificate-canonical-property.md)) property for use in a report. It can be used to prove to the originator that the recipient actually received the message, which a delivery report does not necessarily indicate.
  
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

