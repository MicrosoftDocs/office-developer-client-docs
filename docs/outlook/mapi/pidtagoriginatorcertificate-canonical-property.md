---
title: "PidTagOriginatorCertificate Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagOriginatorCertificate
api_type:
- COM
ms.assetid: 65f890d8-9d25-408e-ab29-89991278b92d
description: "Contains an ASN.1 certificate for the message originator for Outlook 2013 and Outlook 2016."
---

# PidTagOriginatorCertificate Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an ASN.1 certificate for the message originator.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGINATOR_CERTIFICATE  <br/> |
|Identifier:  <br/> |0x0022  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MIME  <br/> |
   
## Remarks

This property is a copy of the originator's **PR_USER_CERTIFICATE** ([PidTagUserCertificate](pidtagusercertificate-canonical-property.md)) property.
  
## Related resources

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

