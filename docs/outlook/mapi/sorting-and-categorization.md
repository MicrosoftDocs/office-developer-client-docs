---
title: "Sorting and Categorization"
description: Outlines sorting and configuration in Outlook 2013 and 2016. There are also links to reference materials.
manager: soliver
ms.date: 11/16/2014
ms.audience: Developer
ms.localizationpriority: medium
api_type:
- COM
ms.assetid: 853c48e4-ef5b-49da-b281-f72784c598ce
 
 
---

# Sorting and Categorization

 
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Sorting a table places rows in an order that makes sense for its viewer. For example, one viewer might prefer to see the contents table of a folder sorted by message subject so that all the threads of a conversation are together while another viewer might want the messages sorted by the name of the sender. A newly instantiated table is not necessarily sorted in any particular order. 
  
There are two types of sorting:
  
- Standard sorting
    
- Categorized sorting 
    
With standard sorting, all of the rows are displayed in a flat list using one or more columns as a sort key. With categorized sorting, the rows are displayed hierarchically with one or more columns as the sort key. Within each category, there is a special heading row that contains the following columns.
  
- The column or columns that make up the sort key
    
- **PR_CONTENT_COUNT** ([PidTagContentCount](pidtagcontentcount-canonical-property.md))
    
- **PR_CONTENT_UNREAD** ([PidTagContentUnreadCount](pidtagcontentunreadcount-canonical-property.md))
    
- **PR_INSTANCE_KEY** ([PidTagInstanceKey](pidtaginstancekey-canonical-property.md))
    
- **PR_DEPTH** ([PidTagDepth](pidtagdepth-canonical-property.md))
    
- **PR_ROW_TYPE** ([PidTagRowType](pidtagrowtype-canonical-property.md)) 
    
Indented under the heading row are all the rows from the table that contain columns with values that match the sort key. These rows are called the leaf rows. Leaf rows contain all the columns in the column set minus the sort key columns. 
  
The contents tables of folders often support categorized sorting in addition to standard sorting. The contents tables of address book containers typically support only standard sorting. 
  
A category can have two states: collapsed and expanded. When a category is in the collapsed state, only the heading row is returned from [IMAPITable::QueryRows](imapitable-queryrows.md). When a category is in the expanded state, all of the rows related to the category are returned. This includes the heading row and the leaf rows. 
  
Each category in a table view can be expanded or collapsed independently. That is, not all categories must be in the same state at the same time; some categories can be collapsed while others are expanded. 
  
The user of a categorized table decides how it is displayed. One common option is to use a control provided in the Windows SDK called the treeview control. Treeview controls are list boxes that support information in a tree-like structure. Heading rows for categories in the expanded state are marked with a minus sign while heading rows for categories in the collapsed state are marked with a plus sign. Expanded categories are displayed with the leaf rows indented under the heading rows. 
  
To collapse and expand a category, a client application or service provider uses the following [IMAPITable : IUnknown](imapitableiunknown.md) methods: 
  
- [IMAPITable::GetCollapseState](imapitable-getcollapsestate.md)
    
- [IMAPITable::SetCollapseState](imapitable-setcollapsestate.md)
    
- [IMAPITable::ExpandRow](imapitable-expandrow.md)
    
- [IMAPITable::CollapseRow](imapitable-collapserow.md)
    
For more information about sorting the threads of a conversation see the following topics:
  
- [SSortOrder](ssortorder.md)
    
- [PidTagSubject Canonical Property](pidtagsubject-canonical-property.md)
    
- [PidTagSubjectPrefix Canonical Property](pidtagsubjectprefix-canonical-property.md)
    
- [PidTagNormalizedSubject Canonical Property](pidtagnormalizedsubject-canonical-property.md)
    
- [PidTagConversationTopic Canonical Property](pidtagconversationtopic-canonical-property.md)
    
- [PidTagConversationIndex Canonical Property](pidtagconversationindex-canonical-property.md)
    
- [ScCreateConversationIndex](sccreateconversationindex.md)
    
- [Sorting Tables After Setting Columns and Restrictions](sorting-tables-after-setting-columns-and-restrictions.md)
    
## See also



[MAPI Tables](mapi-tables.md)

