---
title: "PidTagMessageDeliveryTime Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagMessageDeliveryTime
api_type:
- HeaderDef
ms.assetid: 4f9d44f2-4faa-4f16-9e33-22f80c17db85
description: "Last modified: March 09, 2015"
---

# PidTagMessageDeliveryTime Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the date and time when a message was delivered. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_MESSAGE_DELIVERY_TIME  <br/> |
|Identifier:  <br/> |0x0E06  <br/> |
|Data type:  <br/> |PT_SYSTIME  <br/> |
|Area:  <br/> |Message time  <br/> |
   
## Remarks

This property describes the time the message was stored at the server, rather than the download time when the transport provider copied the message from the server to the local store.
  
## Related Resources

### Protocol Specifications

[[MS-OXOMSG]](http://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for e-mail message objects.
    
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

