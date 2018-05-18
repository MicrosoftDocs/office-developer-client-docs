---
title: "PidTagRtfSyncBodyCrc Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagRtfSyncBodyCrc
api_type:
- COM
ms.assetid: 95db4837-400f-476f-b313-60e8baa1c6d1
description: "Last modified: March 09, 2015"
---

# PidTagRtfSyncBodyCrc Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the cyclical redundancy check (CRC) computed for the message text.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_RTF_SYNC_BODY_CRC  <br/> |
|Identifier:  <br/> |0x1006  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |MAPI message  <br/> |
   
## Remarks

The [RTFSync](rtfsync.md) function computes the CRC by using only the characters that it considers to be significant to the message. For example, some white space and other ignorable characters are omitted from the CRC. 
  
This property is a Rich Text Format (RTF) auxiliary property. These properties are used by the **RTFSync** function and are not intended to be used directly by client applications. 
  
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

