---
title: "PidTagSelectable Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagSelectable
api_type:
- COM
ms.assetid: eeecd957-dd50-4849-9698-8bc7106301e9
description: "Last modified: March 09, 2015"
---

# PidTagSelectable Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains TRUE if the entry in the one-off table can be selected. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SELECTABLE  <br/> |
|Identifier:  <br/> |0x3609  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Address book container  <br/> |
   
## Remarks

This property is used primarily for visual formatting of a one-off table. Templates can be grouped by creating an entry that indicates the heading for the group. Setting this property to FALSE for the heading ensures that the user can select only the actual templates in the group and not this heading entry. 
  
This property applies only to a one-off table, not to an address book hierarchy table. 
  
MAPI allows an address book provider to group items visually by two means. First, certain rows can function as headings by being unselectable. Second, the selectable items can be indented relative to their headings by using the **PR_DEPTH** ([PidTagDepth](pidtagdepth-canonical-property.md)) property. This property is used in such grouping to indicate whether or not this item can be selected from a list to create a one-off address. For example, if a client has several templates for building fax addresses, it can display them as follows: 
  
FAX templates (depth 0, not selectable)
  
 Local (depth 1, selectable) 
  
 Long-distance (depth 1, selectable) 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOABKT]](http://msdn.microsoft.com/library/cd5a3e78-1eeb-4a75-88eb-e82c8c96ff31%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for address book templates.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[IABLogon::GetOneOffTable](iablogon-getoneofftable.md)
  
[PidTagFolderType Canonical Property](pidtagfoldertype-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

