---
title: "PidTagIpmTaskEntryId Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagIpmTaskEntryId
api_type:
- HeaderDef
ms.assetid: ec8b7486-b547-4a4e-96e5-1fc825b23f3d
description: "Last modified: March 09, 2015"
---

# PidTagIpmTaskEntryId Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the **EntryID** of the Outlook Tasks folder. 
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_IPM_TASK_ENTRYID  <br/> |
|Identifier:  <br/> |0x36D4  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Folder  <br/> |
   
## Remarks

This property is read or written by using the Property and Stream Object protocol. It is read from and written to the Inbox or Root folder. The implementation must use the Inbox folder when the store is that of the primary messaging user, and it must use the Root folder when the store is that of a delegate user.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOSFLD]](https://msdn.microsoft.com/library/a60e9c16-2ba8-424b-b60c-385a8a2837cb%28Office.15%29.aspx)
  
> Specifies the properties and operations for creating and locating the special folders in a mailbox.
    
[[MS-OXODLGT]](https://msdn.microsoft.com/library/01a89b11-9c43-4c40-b147-8f6a1ef5a44f%28Office.15%29.aspx)
  
> Specifies methods for connecting to and configuring mailboxes as delegates, and interactions with message and calendar objects when they act on behalf of another user.
    
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

