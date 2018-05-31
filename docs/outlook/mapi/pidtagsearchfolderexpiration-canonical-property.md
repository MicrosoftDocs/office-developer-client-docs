---
title: "PidTagSearchFolderExpiration Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagSearchFolderExpiration
api_type:
- COM
ms.assetid: e5746090-c850-4e95-b1e7-a07e42c87179
description: "Last modified: March 09, 2015"
---

# PidTagSearchFolderExpiration Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the time at which the search folder container will be stale and should be updated or recreated.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_WB_SF_EXPIRATION  <br/> |
|Identifier:  <br/> |0x683A  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Search  <br/> |
   
## Remarks

This property must be formatted as the number of minutes since midnight Coordinated Universal Time (UTC) January 1, 1601.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXOSRCH]](http://msdn.microsoft.com/library/c72e49b8-78c7-4483-ad65-e46e9133673b%28Office.15%29.aspx)
  
> Specifies the properties and operations for manipulating a search folder list configuration.
    
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

