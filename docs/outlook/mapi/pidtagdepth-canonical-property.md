---
title: "PidTagDepth Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagDepth
api_type:
- HeaderDef
ms.assetid: 04d444a5-e97f-48e6-89a5-8a6cb2136408
description: "Last modified: March 09, 2015"
---

# PidTagDepth Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an integer that represents the relative level of indentation, or depth, of an object in a hierarchy table.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_DEPTH  <br/> |
|Identifier:  <br/> |0x3005  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI common  <br/> |
   
## Remarks

This property can also specify the categorization level of a row in a contents table or the hierarchy depth in a hierarchy table. The depth is zero-based, where zero represents the leftmost category. In all cases, the property value represents a relative value rather than an absolute value. In the hierarchy table, for example, the depth value is relative to the container from which the hierarchy table was retrieved. The depth does not represent an absolute depth from the root container. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCTABL]](https://msdn.microsoft.com/library/d33612dc-36a8-4623-8a26-c156cf8aae4b%28Office.15%29.aspx)
  
> Includes permissible operations for the core table objects.
    
[[MS-OXOABK]](https://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[PidTagObjectType Canonical Property](pidtagobjecttype-canonical-property.md)
  
[PidTagSelectable Canonical Property](pidtagselectable-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

