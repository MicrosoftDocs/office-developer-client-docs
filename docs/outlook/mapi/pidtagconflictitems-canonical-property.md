---
title: "PidTagConflictItems Canonical Property" 
description: Outlines the PidTagConflictItems canonical property, which contains one or more entry IDs of items that have been involved in an automatic conflict resolution.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagConflictItems
api_type:
- HeaderDef
ms.assetid: 0d147827-f0e2-dcc1-4427-c4a2f48ca801
---

# PidTagConflictItems Canonical Property

**Applies to**: Outlook 2013 | Outlook 2016
  
Contains one or more entry IDs of items that have been involved in an automatic conflict resolution.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_CONFLICT_ITEMS  <br/> |
|Identifier:  <br/> |0x1098  <br/> |
|Property type:  <br/> |PT_MV_BINARY  <br/> |
|Area:  <br/> |ICS  <br/> |

## Remarks

The types of standard Microsoft Outlook items that support automatic conflict resolution include the following standard item types: appointment items, contact items, journal items, mail items, meeting items, sticky note items, and task items. An item belonging to a message class that derives from one of these standard item types also supports automatic conflict resolution. In Microsoft Outlook 2003 and Microsoft Office Outlook 2007, when Outlook synchronizes items and considers that there is a possibility that the resultant copy may not contain all essential data, Outlook stores the conflicting copies in the **Conflicts** folder, under the **Sync Issues** folder.
  
> [!NOTE]
> **Sync Issues** and its subfolders are hidden until you click **Folder List** on the **Go** menu.
  
An item exposes the **PR_CONFLICT_ITEMS** property if it is one of the item types that support automatic conflict resolution, has won in a conflict resolution, or was placed in the **Conflicts** folder because of a conflict resolution. The folder in which the item is placed determines the content of **PR_CONFLICT_ITEMS**. If the item is located in some folder other than the **Conflicts** folder, and the item exposes the **PR_CONFLICT_ITEMS** property, the item must have won the conflict resolution, and **PR_CONFLICT_ITEMS** would contain one or more entry IDs of those items that lost in the conflict resolution. If the item is located in the **Conflicts** folder and the item exposes the **PR_CONFLICT_ITEMS** property, this item must have lost the conflict resolution, and **PR_CONFLICT_ITEMS** would contain the entry ID of the item that won in the conflict resolution.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.

[[MS-OXCFXICS]](https://msdn.microsoft.com/library/b9752f3d-d50d-44b8-9e6b-608a117c8532%28Office.15%29.aspx)
  
> Handles synchronizing messaging object data between a server and a client.

### Header files

Mapidefs.h
  
> Provides data type definitions.

Mapitags.h
  
> Contains definitions of properties listed as alternate names.

## See also

[About MAPI Additions](about-mapi-additions.md)  
[MAPI Properties](mapi-properties.md)  
[MAPI Canonical Properties](mapi-canonical-properties.md)  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)
