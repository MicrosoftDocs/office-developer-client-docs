---
title: "PidTagRtfSyncPrefixCount Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagRtfSyncPrefixCount
api_type:
- COM
ms.assetid: c2b15ac5-9e89-4ee2-812d-102d0b2ac56e
description: "Last modified: March 09, 2015"
---

# PidTagRtfSyncPrefixCount Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a count of the ignorable characters that appear before the significant characters of the message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_RTF_SYNC_PREFIX_COUNT  <br/> |
|Identifier:  <br/> |0x1010  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI message  <br/> |
   
## Remarks

The count of prefix characters does not include white space.
  
This property is a Rich Text Format (RTF) auxiliary property. RTF auxiliary properties are used by the [RTFSync](rtfsync.md) function and are not intended to be used directly by client applications. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXTNEF]](http://msdn.microsoft.com/library/1f0544d7-30b7-4194-b58f-adc82f3763bb%28Office.15%29.aspx)
  
> Encodes and decodes message and attachment objects to an efficient stream representation.
    
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

