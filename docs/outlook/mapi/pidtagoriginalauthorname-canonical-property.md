---
title: "PidTagOriginalAuthorName Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagOriginalAuthorNam
api_type:
- COM
ms.assetid: beb23742-d844-4d90-9b13-1ad376d4206c
description: "Last modified: March 09, 2015"
---

# PidTagOriginalAuthorName Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the display name of the author of the first version of a message, that is, the message before being forwarded or replied to.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGINAL_AUTHOR_NAME, PR_ORIGINAL_AUTHOR_NAME_A, PR_ORIGINAL_AUTHOR_NAME_W  <br/> |
|Identifier:  <br/> |0x004D  <br/> |
|Data type:  <br/> |PT_UNICODE, PT_STRING8  <br/> |
|Area:  <br/> |Email  <br/> |
   
## Remarks

These properties are examples of the address properties for the author of a message. At first submission of the message, the client application should set these properties to the value of **PR_SENDER_NAME** ([PidTagSenderName](pidtagsendername-canonical-property.md)). It is never changed when the message is forwarded or replied to.
  
The original author properties allow for preservation of information from outside the local messaging domain. When a message arrives from another messaging domain, such as from the Internet, these properties provide a way to ensure that original information is not lost.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCICAL]](http://msdn.microsoft.com/library/a685a040-5b69-4c84-b084-795113fb4012%28Office.15%29.aspx)
  
> Converts between IETF RFC2445, RFC2446, and RFC2447, and appointment and meeting objects.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also



[PidTagDisplayName Canonical Property](pidtagdisplayname-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

