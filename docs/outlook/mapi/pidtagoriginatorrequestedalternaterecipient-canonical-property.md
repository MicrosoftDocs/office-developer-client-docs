---
title: "PidTagOriginatorRequestedAlternateRecipient Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagOriginatorRequestedAlternateRecipient
api_type:
- COM
ms.assetid: c85b7862-18bc-4e17-94db-9097e0ac4a02
description: "Last modified: March 09, 2015"
---

# PidTagOriginatorRequestedAlternateRecipient Canonical Property

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Contains an entry identifier for an alternate recipient designated by the sender.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGINATOR_REQUESTED_ALTERNATE_RECIPIENT  <br/> |
|Identifier:  <br/> |0x0C09  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MIME  <br/> |
   
## Remarks

This property is used in autoforwarded messages. If autoforwarding is not permitted or if no alternate recipient has been designated, a nondelivery report should be generated.
  
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

