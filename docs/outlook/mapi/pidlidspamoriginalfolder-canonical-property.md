---
title: "PidLidSpamOriginalFolder Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidLidSpamOriginalFolder
api_type:
- COM
ms.assetid: 45846fe3-7ab3-4019-98bb-fe615889c31c
description: "Last modified: March 09, 2015"
---

# PidLidSpamOriginalFolder Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Indicates which folder a message was in before it was filtered into the junk email folder.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |dispidSpamOriginalFolder  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x0000859C  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Spam  <br/> |
   
## Remarks

The value of this property is the **EntryID** of the folder that contained the message before it was moved. This property should be set when a message is marked as spam. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXCSPAM]](https://msdn.microsoft.com/library/522f8587-4aed-4cd6-831b-40bd87862189%28Office.15%29.aspx)
  
> Enables the handling of allow/block lists and the determination of junk email messages.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

