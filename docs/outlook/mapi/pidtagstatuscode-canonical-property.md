---
title: "PidTagStatusCode Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagStatusCode
api_type:
- COM
ms.assetid: e29190c5-52c3-4ef7-98db-699487c54325
description: "Last modified: March 09, 2015"
---

# PidTagStatusCode Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a bitmask of flags that indicate the current status of a session resource. All service providers set status codes as does MAPI to report on the status of the subsystem, the MAPI spooler, and the integrated address book.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_STATUS_CODE  <br/> |
|Identifier:  <br/> |0x3E04  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI status  <br/> |
   
## Remarks

The status code must appear in the Mapisvc.inf file for all providers. 
  
Status objects are implemented by MAPI and by all service providers. There are two sets of valid values for status codes, one set for all status objects and another set for transport providers only. All status objects can set this property to the following values:
  
STATUS_AVAILABLE 
  
> Indicates that the resource is operational.
    
STATUS_FAILURE 
  
> Indicates that the resource is experiencing a problem. For service providers, STATUS_FAILURE indicates that the provider might soon be shut down to end the current session.
    
STATUS_OFFLINE 
  
> Indicates that only local data or services are available.
    
Transport providers can also set their status objects' **PR_STATUS_CODE** properties to the following values: 
  
STATUS_INBOUND_ACTIVE 
  
> Indicates that the transport provider is receiving an inbound message. 
    
STATUS_INBOUND_ENABLED 
  
> Indicates that the transport provider can receive inbound messages.
    
STATUS_INBOUND_FLUSH 
  
> Indicates that the transport provider is downloading messages from the inbound queue.
    
STATUS_OUTBOUND_ACTIVE 
  
> Indicates that the transport provider is receiving an outbound message. 
    
STATUS_OUTBOUND_ENABLED 
  
> Indicates that the transport provider can handle outbound messages.
    
STATUS_OUTBOUND_FLUSH 
  
> Indicates that the transport provider is uploading messages from its outbound queue.
    
STATUS_REMOTE_ACCESS 
  
> Indicates that the transport provider supports remote access.
    
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[PidTagStatusString Canonical Property](pidtagstatusstring-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

