---
title: "PidTagSpamThreshold Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
ms.assetid: 2b2d6b8e-e3dd-4a9b-8bb5-53add675605d
description: "A long value that indicates the level of spam filtering."
---

# PidTagSpamThreshold Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
A long value that indicates the level of spam filtering.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_SPAM_THRESHOLD  <br/> |
|Long ID (LID):  <br/> | 0x041B  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Spam  <br/> |
   
## Values

The values for spam filtering are as follows:
  
|**Spam Level**|**Value**|
|:-----|:-----|
|None  <br/> |0xFFFFFFFF  <br/> |
|Low  <br/> |0x00000006  <br/> |
|Medium  <br/> |0x00000005  <br/> |
|High  <br/> |0x00000003  <br/> |
   
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Microsoft Exchange Server protocol specifications.
    
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

