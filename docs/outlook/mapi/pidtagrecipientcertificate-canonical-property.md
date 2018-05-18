---
title: "PidTagRecipientCertificate Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagRecipientCertificate
api_type:
- COM
ms.assetid: 7c5c749e-5463-4935-85b5-32219d06f782
description: "Last modified: March 09, 2015"
---

# PidTagRecipientCertificate Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a message recipient's ASN.1 certificate for use in a report.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_RECIPIENT_CERTIFICATE  <br/> |
|Identifier:  <br/> |0x0C13  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI Recipient  <br/> |
   
## Remarks

This property is a copy of the recipient's **PR_USER_CERTIFICATE** ([PidTagUserCertificate](pidtagusercertificate-canonical-property.md)) property for use in a report. It can be used to prove to the originator that the recipient actually received the message, which a delivery report does not necessarily indicate.
  
## Related Resources

### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

