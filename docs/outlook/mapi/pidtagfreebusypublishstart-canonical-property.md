---
title: "PidTagFreeBusyPublishStart Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagFreeBusyPublishStart
api_type:
- HeaderDef
ms.assetid: d059f913-3d61-4bec-8215-5b07f0fba488
description: "Last modified: March 09, 2015"
---

# PidTagFreeBusyPublishStart Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the start time of the publishing range.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_FREEBUSY_PUBLISH_START  <br/> |
|Identifier:  <br/> |0x6847  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Free/Busy  <br/> |
   
## Remarks

The value for this property is the number of minutes since midnight, January 1, 1601 in Coordinated Universal Time (UTC).
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOPFFB]](http://msdn.microsoft.com/library/1a527299-7211-4d27-a74c-b69bd0746320%28Office.15%29.aspx)
  
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

