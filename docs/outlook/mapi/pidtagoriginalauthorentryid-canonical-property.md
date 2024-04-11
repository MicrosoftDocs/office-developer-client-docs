---
title: "PidTagOriginalAuthorEntryId Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagOriginalAuthorEntryId
api_type:
- COM
ms.assetid: 34654660-b003-42f5-9fcd-24ebaccd735d
description: "Contains the entry identifier of the author of the first version of a message, which is the message before being forwarded or replied to."
---

# PidTagOriginalAuthorEntryId Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the entry identifier of the author of the first version of a message, that is, the message before being forwarded or replied to.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGINAL_AUTHOR_ENTRYID  <br/> |
|Identifier:  <br/> |0x004C  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

This property is one of the address properties for the author of a message. At first submission of the message, the client application should set this property to the value of **PR_SENDER_ENTRYID** ([PidTagSenderEntryId](pidtagsenderentryid-canonical-property.md)). It is never changed when the message is forwarded or replied to. 
  
The original author property allows for preservation of information from outside the local messaging domain. When a message arrives from another messaging domain, such as from the Internet, this property provides a way to ensure that original information is not lost.
  
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

