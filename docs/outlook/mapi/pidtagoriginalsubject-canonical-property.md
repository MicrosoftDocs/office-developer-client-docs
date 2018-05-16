---
title: "PidTagOriginalSubject Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagOriginalSubject
api_type:
- COM
ms.assetid: 8668ba4f-3236-4a87-a5aa-9cf7eea3d87b
description: "Last modified: March 09, 2015"
---

# PidTagOriginalSubject Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the subject of an original message for use in a report about the message.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_ORIGINAL_SUBJECT, PR_ORIGINAL_SUBJECT_A, PR_ORIGINAL_SUBJECT_W  <br/> |
|Identifier:  <br/> |0x0049  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

These properties are originally set to the same value as the **PR_SUBJECT** ( [PidTagSubject](pidtagsubject-canonical-property.md)) property.
  
The subject properties are typically small strings of fewer than 256 characters, and a message store provider is not obligated to support the Object Linking and Embedding (OLE) **IStream** interface on them. The client should always attempt access through the **IMAPIProp** interface first, and resort to **IStream** only if **MAPI_E_NOT_ENOUGH_MEMORY** is returned. 
  
## Related Resources

### Protocol Specifications

[[MS-OXPROPS]](http://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCFXICS]](http://msdn.microsoft.com/library/b9752f3d-d50d-44b8-9e6b-608a117c8532%28Office.15%29.aspx)
  
> Handles synchronizing messaging object data between a server and a client.
    
[[MS-OXOMSG]](http://msdn.microsoft.com/library/daa9120f-f325-4afb-a738-28f91049ab3c%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible on e-mail message objects.
    
### Header Files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as alternate names.
    
## See also

#### Concepts

[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

