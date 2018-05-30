---
title: "PidTagSpoolerStatus Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagSpoolerStatus
api_type:
- COM
ms.assetid: a10d86fc-3a73-49dc-b974-ed852ec715e9
description: "Last modified: March 09, 2015"
---

# PidTagSpoolerStatus Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the status of the message based on information that is available to the MAPI spooler.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SPOOLER_STATUS  <br/> |
|Identifier:  <br/> |0x0E10  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI non-transmittable  <br/> |
   
## Remarks

This property is computed by MAPI on message objects.
  
This property appears on inbound messages only and is reserved in all other cases. It indicates whether or not a message has been delivered to its final location or whether a messaging hook provider potentially deleted the message while rerouting it.
  
Client applications should never set this property. For an inbound message, a client or service provider can call [IMAPIProp::GetProps](imapiprop-getprops.md) on this property to determine the message status. The value S_OK indicates that the message was successfully delivered to the message store. The value MAPI_E_OBJECT_DELETED indicates that the message was deleted and was never committed to the store. 
  
Message store providers should support this property on messages, recipient tables, and the outgoing queue table. Clients and providers should be able to set columns on the outgoing queue table and restrict based on this property.
  
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

