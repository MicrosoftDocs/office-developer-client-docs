---
title: "PidTagConversationIndex Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagConversationIndex
api_type:
- HeaderDef
ms.assetid: c65cdda7-9515-4da9-be75-43ebf45a02df
description: "Last modified: March 09, 2015"
---

# PidTagConversationIndex Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a binary value that indicates the relative position of this message within a conversation thread. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_CONVERSATION_INDEX  <br/> |
|Identifier:  <br/> |0x0071  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

A conversation thread represents a series of messages and replies. This property is usually implemented using concatenated time stamp values. Its use is optional, even if **PR_CONVERSATION_TOPIC** ([PidTagConversationTopic](pidtagconversationtopic-canonical-property.md)) is set. 
  
MAPI provides the [ScCreateConversationIndex](sccreateconversationindex.md) function to create or update a conversation index. The function takes the current index value as a counted byte array and returns the index value with a time stamp concatenated onto the end. A message representing a reply to another message should use **ScCreateConversationIndex** to update this property. 
  
A message store provider has the option of assuring that **PR_CONVERSATION_INDEX** is always set on incoming or outgoing messages. It can do this by calling **ScCreateConversationIndex**, either with the existing value if this property is set or with NULL if it is not. This action should be taken before [IMAPIProp::SaveChanges](imapiprop-savechanges.md) is called. 
  
All messages that have the same value for **PR_CONVERSATION_TOPIC** can be sorted on this property to reveal the hierarchical relationship of the messages. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOMSG]](https://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible on email message objects.
    
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

