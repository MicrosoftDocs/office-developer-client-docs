---
title: "PidTagJunkThreshold Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagJunkThreshold
api_type:
- HeaderDef
ms.assetid: 8067e2b5-02df-4b96-8f66-509f5a48c8aa
description: "Last modified: March 09, 2015"
---

# PidTagJunkThreshold Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Indicates how aggressively incoming mail should be sent to the Junk Email folder.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_JUNK_THRESHOLD  <br/> |
|Identifier:  <br/> |0x6101  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Spam  <br/> |
   
## Remarks

This property corresponds to the high / low / none filter setting. A value of "0xFFFFFFFF" indicates that spam filtering should not be applied, however block lists must still be applied. A value of "0x80000000" indicates that all mail is spam except those messages from senders on the trusted senders list or sent to recipients on the trusted recipients list. Values for this are as follows:
  
|**Value**|**Description**|
|:-----|:-----|
|0xFFFFFFFF  <br/> |No spam filtering  <br/> |
|0x00000006  <br/> |Low spam filtering  <br/> |
|0x00000003  <br/> |High spam filtering  <br/> |
|0x80000000  <br/> |Trusted Lists Only  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCSPAM]](https://msdn.microsoft.com/library/522f8587-4aed-4cd6-831b-40bd87862189%28Office.15%29.aspx)
  
> Enables the handling of allow/block lists and the determination of junk email messages.
    
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

