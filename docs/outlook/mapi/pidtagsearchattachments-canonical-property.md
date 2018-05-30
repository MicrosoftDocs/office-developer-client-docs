---
title: "PidTagSearchAttachments Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 534c3881-e12f-f228-7760-788fe2b72ae8
description: "Last modified: March 09, 2015"
---

# PidTagSearchAttachments Canonical Property

  
  
**Applies to**: Outlook 
  
Contains a Unicode string that is being queried in attachment contents on the store.
  
## 

|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SEARCH_ATTACHMENTS_W  <br/> |
|Identifier:  <br/> |0x0EA5  <br/> |
|Property type:  <br/> |PT_UNICODE  <br/> |
|Area:  <br/> |Search  <br/> |
   
## Related resources

> [!NOTE]
> This MAPI restriction tag, used when you are searching for attachment contents, might not be defined in the downloadable header file that you currently have. You can add it to your code by using the following value: >  `#define PR_SEARCH_ATTACHMENTS_W PROP_TAG(PT_UNICODE, 0x0EA5)`
  
### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Microsoft Exchange Server protocol specifications.
    
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

