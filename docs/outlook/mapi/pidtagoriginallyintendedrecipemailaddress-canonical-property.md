---
title: "PidTagOriginallyIntendedRecipEmailAddress Canonical Property"
description: Outlines the PidTagOriginallyIntendedRecipEmailAddress canonical property, which holds the email address of the intended recipient of an autoforwarded message.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagOriginallyIntendedRecipEmailAddress
api_type:
- COM
ms.assetid: 6a85b695-731a-4401-9c9c-fda6bc308558
---

# PidTagOriginallyIntendedRecipEmailAddress Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the email address of the originally intended recipient of an autoforwarded message.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGINALLY_INTENDED_RECIP_EMAIL_ADDRESS, PR_ORIGINALLY_INTENDED_RECIP_EMAIL_ADDRESS_A, PR_ORIGINALLY_INTENDED_RECIP_EMAIL_ADDRESS_W  <br/> |
|Identifier:  <br/> |0x007C  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |Server  <br/> |
   
## Remarks

These properties are examples of the address properties for the originally intended message recipient. They must be set by the automatic agent that has forwarded the message.
  
These properties correspond to the X.400 report per-recipient attribute.
  
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

