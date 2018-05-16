---
title: "PidTagOriginatorCertificate Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagOriginatorCertificate
api_type:
- COM
ms.assetid: 65f890d8-9d25-408e-ab29-89991278b92d
description: "Last modified: March 09, 2015"
---

# PidTagOriginatorCertificate Canonical Property

  
  
**Applies to**: Outlook 
  
Contains an ASN.1 certificate for the message originator.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGINATOR_CERTIFICATE  <br/> |
|Identifier:  <br/> |0x0022  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MIME  <br/> |
   
## Remarks

This property is a copy of the originator's **PR_USER_CERTIFICATE** ( [PidTagUserCertificate](pidtagusercertificate-canonical-property.md)) property.
  
## Related Resources

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

