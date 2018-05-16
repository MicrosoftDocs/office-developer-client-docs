---
title: "PidTagOriginalSentRepresentingEntryId Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagOriginalSentRepresentingEntryId
api_type:
- COM
ms.assetid: ece3df57-47f3-4d27-854f-b511c920ac75
description: "Last modified: March 09, 2015"
---

# PidTagOriginalSentRepresentingEntryId Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the entry identifier of the messaging user on whose behalf the original message was sent.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGINAL_SENT_REPRESENTING_ENTRYID  <br/> |
|Identifier:  <br/> |0x005E  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

This property is one of the address properties for the original represented sender of a message. It is used in a conversation thread.
  
A client application sending a message on behalf of another client should set this property to the value of the **PR_SENT_REPRESENTING_ENTRYID** ( [PidTagSentRepresentingEntryId](pidtagsentrepresentingentryid-canonical-property.md)) property at the first submission of the message. Once set, it should never be changed.
  
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

