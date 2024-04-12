---
title: "PidTagFreeBusyPublishEnd Canonical Property"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagFreeBusyPublishEnd
api_type:
- HeaderDef
ms.assetid: df239741-6a63-4cd4-9bbb-42c0f5c668a5
description: "Contains the end time of the publishing range. This value is expressed as the number of minutes since midnight, January 1, 1601, UTC."
---

# PidTagFreeBusyPublishEnd Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the end time of the publishing range.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_FREEBUSY_PUBLISH_END  <br/> |
|Identifier:  <br/> |0x6848  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Free/Busy  <br/> |
   
## Remarks

The value for this property is computed by adding the value of **PR_FREEBUSY_COUNT_MONTHS** ([PidTagFreeBusyCountMonths](pidtagfreebusycountmonths-canonical-property.md)) to the start date of the publishing range. This value is expressed as the number of minutes since midnight, January 1, 1601 in Coordinated Universal Time (UTC).
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOPFFB]](https://msdn.microsoft.com/library/1a527299-7211-4d27-a74c-b69bd0746320%28Office.15%29.aspx)
  
> Publishes the availability of a user or resource.
    
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

