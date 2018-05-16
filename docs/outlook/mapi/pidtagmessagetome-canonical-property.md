---
title: "PidTagMessageToMe Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagMessageToMe
api_type:
- HeaderDef
ms.assetid: aeb0fa71-f471-46c5-ad9c-f8afb3fed533
description: "Last modified: March 09, 2015"
---

# PidTagMessageToMe Canonical Property

  
  
**Applies to**: Outlook 
  
Contains TRUE if this messaging user is specifically named as a primary (To) recipient of this message and is not part of a distribution list. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_MESSAGE_TO_ME  <br/> |
|Identifier:  <br/> |0x0057  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

This property provides a convenient way to determine whether the user name appears explicitly in the primary recipient list, without examining all entries in the list. 
  
This property also assists automated handling of received messages at the time of receipt. At the transport provider's option, this property either contains FALSE or is not included if the messaging user is not listed directly in the recipient table. 
  
Message delivery resulting from distribution list expansion or a blind carbon copy designation does not cause this property to be set. The recipient must be explicitly named. 
  
Unsent messages generally do not set the **PR_MESSAGE_CC_ME** ( [PidTagMessageCcMe](pidtagmessageccme-canonical-property.md)), **PR_MESSAGE_RECIP_ME** ( [PidTagMessageRecipientMe](pidtagmessagerecipientme-canonical-property.md)), or this property. If they are present in messages the user can access in public message stores, in other users' private stores, in files on disk, or embedded inside other received messages, they generally contain the values to which they were set the last time a transport provider delivered the message. 
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOMSG]](http://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible on e-mail message objects.
    
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

