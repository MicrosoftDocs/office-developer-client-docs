---
title: "PidTagTnefCorrelationKey Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagTnefCorrelationKey
api_type:
- COM
ms.assetid: a7f05c8c-59b4-4d5b-8e70-ebcde5f2ed45
description: "Last modified: March 09, 2015"
---

# PidTagTnefCorrelationKey Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a value that correlates a Transport Neutral Encapsulation Format (TNEF) attachment with a message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_TNEF_CORRELATION_KEY  <br/> |
|Identifier:  <br/> |0x007F  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI envelope  <br/> |
   
## Remarks

It is recommended that TNEF attachment sub-objects expose this property. This property determines whether or not an inbound TNEF file belongs to the message it is attached to. It is used primarily by transport providers and gateways.
  
On an outbound message, the transport provider should compute a binary value unique to that message, or use an existing value that satisfies the uniqueness requirement, such as a message identifier. The transport provider should store this value in this property and then call the [ITnef::AddProps](itnef-addprops.md) method to encapsulate it. The same value should also be stored in the transport envelope in a place defined by the provider, such as the message header. 
  
On an inbound message, the transport provider should call the [ITnef::ExtractProps](itnef-extractprops.md) method to decapsulate the TNEF attachment and then compare this property with the value stored in the transport envelope. If the values match, TNEF should be processed normally, that is, all the properties extracted from the TNEF attachment should be used. If the values do not match, all the properties from the TNEF attachment should be ignored. If this property is not set, the TNEF file should be considered to belong to this message, and the other properties extracted from it should be used. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCFXICS]](http://msdn.microsoft.com/library/b9752f3d-d50d-44b8-9e6b-608a117c8532%28Office.15%29.aspx)
  
> Handles the order and flow for data transfers between a client and server.
    
[[MS-OXCMAIL]](http://msdn.microsoft.com/library/b60d48db-183f-4bf5-a908-f584e62cb2d4%28Office.15%29.aspx)
  
> Converts from Internet standard email conventions to message objects.
    
[[MS-OXTNEF]](http://msdn.microsoft.com/library/1f0544d7-30b7-4194-b58f-adc82f3763bb%28Office.15%29.aspx)
  
> Encodes and decodes message and attachment objects to an efficient stream representation.
    
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

