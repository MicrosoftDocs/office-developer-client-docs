---
title: "PidTagContentCount Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagContentCount
api_type:
- HeaderDef
ms.assetid: 27c75031-a968-4636-98a6-4a5b7422f57c
description: "Last modified: March 09, 2015"
---

# PidTagContentCount Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the number of messages in a folder, as computed by the message store.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_CONTENT_COUNT  <br/> |
|Identifier:  <br/> |0x3602  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Folder  <br/> |
   
## Remarks

This property computed by the message store is used for two different, though related, purposes. On a MapiFolder object, it contains the number of messages in a folder. In a heading row in categorized MAPI tables, it contains the number of non-associated messages in the category corresponding to that heading row.
  
The number contained in this property does not include associated entries in the folder. **PR_CONTENT_UNREAD** ([PidTagContentUnreadCount](pidtagcontentunreadcount-canonical-property.md)) contains the count of unread messages for the folder. A client application can read but not change this property and **PR_CONTENT_UNREAD**. 
  
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

