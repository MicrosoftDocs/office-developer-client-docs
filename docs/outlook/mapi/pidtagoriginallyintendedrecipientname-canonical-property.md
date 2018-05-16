---
title: "PidTagOriginallyIntendedRecipientName Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagOriginallyIntendedRecipientName
api_type:
- COM
ms.assetid: 56c406fb-8778-4f85-bbdc-4cabfa140248
description: "Last modified: March 09, 2015"
---

# PidTagOriginallyIntendedRecipientName Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the encoded name of the originally intended recipient of an autoforwarded message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGINALLY_INTENDED_RECIPIENT_NAME  <br/> |
|Identifier:  <br/> |0x0020  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Server  <br/> |
   
## Remarks

The **PR_ORIGINALLY_INTENDED_RECIPIENT_NAME** property must be set by the automatic agent that has forwarded the message. 
  
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

