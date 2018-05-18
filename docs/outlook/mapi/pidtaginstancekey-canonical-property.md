---
title: "PidTagInstanceKey Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagInstanceKey
api_type:
- HeaderDef
ms.assetid: 14fc5571-acc0-4d75-8598-964aee5ba01c
description: "Last modified: March 09, 2015"
---

# PidTagInstanceKey Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a value that uniquely identifies a row in a table. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_INSTANCE_KEY  <br/> |
|Identifier:  <br/> |0x0FF6  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Table  <br/> |
   
## Remarks

This property is a binary value that uniquely identifies a row in a table view. It is a required column in most tables. If a row is included in two views, there are two different instance keys. The instance key of a row may differ each time the table is opened, but remains constant while the table is open. Rows added while a table is in use do not reuse an instance key that was previously used. 
  
Use the **PR_ENTRYID** ([PidTagEntryId](pidtagentryid-canonical-property.md)) or **PR_RECORD_KEY** ([PidTagRecordKey](pidtagrecordkey-canonical-property.md)) properties to correlate all the rows of an expansion. Use **PR_INSTANCE_KEY** to locate a particular instance within the expansion. 
  
When a multivalued property is expanded in a table, a row is created for each instance of the expansion, that is, for each value of that property. Each row has a unique value for the **PR_INSTANCE_KEY** property, while all the other columns retain their original values throughout the expansion. 
  
In a categorized sort of a table, rows not corresponding to actual data can be added to the result of the sort. Each such row, like all rows in all tables, has its own unique instance key. 
  
 **PR_INSTANCE_KEY** is also used in table event notifications. The **propIndex** and **propPrior** members of the [TABLE_NOTIFICATION](table_notification.md) structure are [SPropValue](spropvalue.md) structures holding **PR_INSTANCE_KEY** values. The **propIndex** member indicates the row that was added or changed. The **propPrior** member indicates the row before the added or changed row ( **PR_NULL** indicates a change to the first row). 
  
This value is not copied as part of the display table. 
  
 **PR_INSTANCE_KEY** is a [MAPIUID](mapiuid.md) structure. All instance keys can be directly compared as binary values. 
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOABK]](http://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
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

