---
title: "PidTagOriginCheck Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagOriginCheck
api_type:
- COM
ms.assetid: 27e0ab2f-b373-41ae-b922-2f45f9671ac6
description: "Contains a binary verification value that enables a delivery report recipient to verify the origin of the original message."
---

# PidTagOriginCheck Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a binary verification value that enables a delivery report recipient to verify the origin of the original message.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGIN_CHECK  <br/> |
|Identifier:  <br/> |0x0027  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Server  <br/> |
   
## Remarks

This property provides a means for a third party, such as a message transfer agent (MTA) or a messaging user receiving a delivery report, to verify the submitted message's origin. If present on a received message, this property should be copied onto any delivery report generated in response to the message.
  
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

