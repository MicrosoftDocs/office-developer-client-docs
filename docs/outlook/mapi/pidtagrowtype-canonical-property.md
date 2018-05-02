---
title: "PidTagRowType Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagRowType
api_type:
- COM
ms.assetid: d57ce5c8-1f60-4709-b86a-4468c4208dfe
description: "Last modified: March 09, 2015"
---

# PidTagRowType Canonical Property

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Contains a value that indicates the type of a row in a table.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ROW_TYPE  <br/> |
|Identifier:  <br/> |0x0FF5  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI non-transmittable  <br/> |
   
## Remarks

This property appears only on contents tables. A category only exists when it has items.
  
This property can have exactly one of the following values:
  
TBL_LEAF_ROW 
  
> Represents actual data, rather than a category row.
    
TBL_EMPTY_CATEGORY 
  
> Not currently used.
    
TBL_EXPANDED_CATEGORY 
  
> The category is expanded; the user interface usually displays this with the minus sign ( - ) next to it.
    
TBL_COLLAPSED_CATEGORY 
  
> The category is collapsed; the user interface usually displays this with the plus sign (+) next to it.
    
## Related Resources

### Protocol Specifications

[[MS-OXCTABL]](http://msdn.microsoft.com/library/d33612dc-36a8-4623-8a26-c156cf8aae4b%28Office.15%29.aspx)
  
> Includes permissible operations for the core table objects.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Reference

[PidTagRowid Canonical Property](pidtagrowid-canonical-property.md)
#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

