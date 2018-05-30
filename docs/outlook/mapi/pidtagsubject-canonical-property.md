---
title: "PidTagSubject Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagSubject
api_type:
- COM
ms.assetid: aa7ba4d9-c5e0-4ce7-a34e-65f675223bc9
description: "Last modified: March 09, 2015"
---

# PidTagSubject Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the full subject of a message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_SUBJECT, PR_SUBJECT_A, PR_SUBJECT_W  <br/> |
|Identifier:  <br/> |0x0037  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

These properties are recommended on all message objects. 
  
These properties are always the full subject text, that is, the concatenation of the prefix and the normalized subject. If there is no prefix, the normalized subject should be the same as the subject. A message store or transport provider uses both these properties and **PR_SUBJECT_PREFIX** ([PidTagSubjectPrefix](pidtagsubjectprefix-canonical-property.md)) properties to compute the normalized subject using the rule described under **PR_NORMALIZED_SUBJECT** ([PidTagNormalizedSubject](pidtagnormalizedsubject-canonical-property.md)).
  
The subject properties are typically small strings of fewer than 256 characters, and a message store provider is not obligated to support the **IStream** interface on them. The client should always attempt access through the **IMAPIProp** interface first, and resort to **IStream** only if **MAPI_E_NOT_ENOUGH_MEMORY** is returned. 
  
For a report, this property contains the original message's subject preceded by a string indicating what has happened to the message.
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](http://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
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

