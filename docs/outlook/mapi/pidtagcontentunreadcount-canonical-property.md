---
title: "PidTagContentUnreadCount Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagContentUnreadCount
api_type:
- HeaderDef
ms.assetid: 4fe207e9-a77f-46b9-b51d-d989847a9d02
description: "Last modified: March 09, 2015"
---

# PidTagContentUnreadCount Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the number of unread messages in a folder, as computed by the message store. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_CONTENT_UNREAD  <br/> |
|Identifier:  <br/> |0x3603  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Folder  <br/> |
   
## Remarks

This property computed by the message store is used for two different, though related, purposes. On a MAPI folder object, it contains the number of messages in a folder. In a heading row in categorized MAPI tables, it contains the number of unread non-associated messages in the category corresponding to that heading row.
  
This property contains the number of messages in the folder contents table for which the MSGFLAG_READ flag is not set in the **PR_MESSAGE_FLAGS** ([PidTagMessageFlags](pidtagmessageflags-canonical-property.md)) property. The **PR_CONTENT_COUNT** ([PidTagContentCount](pidtagcontentcount-canonical-property.md)) property contains the total message count for the folder. The **PR_CONTENT_COUNT** and this property are read-only to clients. 
  
Some client applications display the heading row of a category differently depending on the value of this property. For example, a client can display a category that includes unread messages in bold. This property cannot be used as a category and an attempt to do so results in the MAPI_E_INVALID_PARAMETER value being returned from the [IMAPITable::SortTable](imapitable-sorttable.md) method. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Microsoft Exchange Server protocol specifications.
    
[[MS-OXCFOLD]](https://msdn.microsoft.com/library/c0f31b95-c07f-486c-98d9-535ed9705fbf%28Office.15%29.aspx)
  
> Handles folder operations.
    
[[MS-OXCTABL]](https://msdn.microsoft.com/library/d33612dc-36a8-4623-8a26-c156cf8aae4b%28Office.15%29.aspx)
  
> Includes permissible operations for the core table objects.
    
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

