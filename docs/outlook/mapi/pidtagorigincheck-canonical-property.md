---
title: "PidTagOriginCheck Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagOriginCheck
api_type:
- COM
ms.assetid: 27e0ab2f-b373-41ae-b922-2f45f9671ac6
description: "Last modified: March 09, 2015"
---

# PidTagOriginCheck Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a binary verification value that enables a delivery report recipient to verify the origin of the original message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGIN_CHECK  <br/> |
|Identifier:  <br/> |0x0027  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Server  <br/> |
   
## Remarks

This property provides a means for a third party, such as a message transfer agent (MTA) or a messaging user receiving a delivery report, to verify the submitted message's origin. If present on a received message, this property should be copied onto any delivery report generated in response to the message.
  
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

