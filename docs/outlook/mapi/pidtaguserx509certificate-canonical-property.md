---
title: "PidTagUserX509Certificate Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagUserX509Certificate
api_type:
- COM
ms.assetid: 278bb9e4-3ff6-4bef-b208-7924f7a5e9b1
description: "Last modified: March 09, 2015"
---

# PidTagUserX509Certificate Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains X.509 version 3 security certificates for a messaging user. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_USER_X509_CERTIFICATE  <br/> |
|Identifier:  <br/> |0x3A70  <br/> |
|Data type:  <br/> |PT_MV_BINARY  <br/> |
|Area:  <br/> |MAPI mail user  <br/> |
   
## Remarks

This property is used by applications that utilize public-key security. It holds a binary representation of one or more X.509 version 3 security certificates. 
  
Various applications and clients can use this property for their own security certificates. The binary format of the X.509 data can vary among vendors. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOABK]](https://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
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

