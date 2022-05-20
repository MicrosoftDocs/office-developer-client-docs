---
title: "PidTagInitialDetailsPane Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagInitialDetailsPane
api_type:
- HeaderDef
ms.assetid: c4712133-6fbd-4c50-a258-5f4317120476
description: "Indicates the page of a display template to display first. This property must not be defined for any objects in an Offline Address Book."
---

# PidTagInitialDetailsPane Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Indicates the page of a display template to display first.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_INITIAL_DETAILS_PANE  <br/> |
|Identifier:  <br/> |0x3F08  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI Display Tables  <br/> |
   
## Remarks

It must be present on all address book objects on an Name Service Provider Interface (NSPI) server, and must have the value zero (0). It must not be defined for any objects in an Offline Address Book.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOABK]](https://msdn.microsoft.com/library/f4cf9b4c-9232-4506-9e71-2270de217614%28Office.15%29.aspx)
  
> Specifies the properties and operations for lists of users, contacts, groups, and resources.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

