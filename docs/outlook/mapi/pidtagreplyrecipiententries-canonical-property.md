---
title: "PidTagReplyRecipientEntries Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagReplyRecipientEntries
api_type:
- COM
ms.assetid: a903fd22-a3f2-464f-99b0-c087e211b124
description: "Contains a sized array of entry identifiers for recipients that are to get a reply. This property contains a structure and is not a multivalued property."
---

# PidTagReplyRecipientEntries Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a sized array of entry identifiers for recipients that are to get a reply.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_REPLY_RECIPIENT_ENTRIES  <br/> |
|Identifier:  <br/> |0x004F  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |MAPI envelope  <br/> |
   
## Remarks

This property contains a [FLATENTRYLIST](flatentrylist.md) structure and is not a multivalued property. 
  
When this property is not present, a reply is sent only to the user identified by the **PR_SENDER_ENTRYID** ([PidTagSenderEntryId](pidtagsenderentryid-canonical-property.md)) property. When this and the **PR_REPLY_RECIPIENT_NAMES** ([PidTagReplyRecipientNames](pidtagreplyrecipientnames-canonical-property.md)) properties are defined, the reply is sent to all of the recipients identified by these two properties. A transport provider uses these properties to override the usual reply logic.
  
If either this property or the **PR_REPLY_RECIPIENT_NAMES** property is set, the other property must be set also. These properties must contain the same number of recipients, and they must contain them in the same order. Failure to observe these requirements can cause unpredictable results. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOMSG]](https://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible on email messages.
    
[[MS-OXCMAIL]](https://msdn.microsoft.com/library/b60d48db-183f-4bf5-a908-f584e62cb2d4%28Office.15%29.aspx)
  
> Converts from Internet standard email conventions to message objects.
    
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

