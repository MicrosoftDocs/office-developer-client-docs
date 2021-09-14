---
title: "PidTagRtfCompressed Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- MAPI.PidTagRtfCompressed
api_type:
- COM
ms.assetid: fd0ccb88-55ce-4d7c-9573-6e5d6239b6a8
description: "Last modified: March 09, 2015"
---

# PidTagRtfCompressed Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the Rich Text Format (RTF) version of the message text, usually in compressed form. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_RTF_COMPRESSED  <br/> |
|Identifier:  <br/> |0x1009  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Email  <br/> |
   
## Remarks

This property contains the same message text as the **PR_BODY** ([PidTagBody](pidtagbody-canonical-property.md)) property but in RTF. 
  
Message text in RTF is normally stored in compressed form. However, some systems do not compress formatted text. To accommodate them, MAPI provides the dwMagicUncompressedRTF value for a stream header to identify uncompressed RTF, and the **STORE_UNCOMPRESSED_RTF** flag in **PR_STORE_SUPPORT_MASK** ([PidTagStoreSupportMask](pidtagstoresupportmask-canonical-property.md)) for the message store to indicate it can store uncompressed RTF. 
  
To obtain the contents of this property, call **OpenProperty**, then call [WrapCompressedRTFStream](wrapcompressedrtfstream.md) with the **MAPI_READ** flag. To write into this property, open it with the **MAPI_MODIFY** and **MAPI_CREATE** flags. This ensures that the new data completely replace any old data and that the writes are performed using the minimum number of store updates. 
  
Message stores that support RTF ignore any changes to white space in the message text. When **PR_BODY** is stored for the first time, the message store also generates and stores this property. If the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method is subsequently called and **PR_BODY** has been modified, the message store calls the [RTFSync](rtfsync.md) function to ensure synchronization with the RTF version. If only white space has been changed, the properties are left unchanged. This preserves any nontrivial RTF formatting when the message travels through non-RTF-aware clients and messaging systems. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCMSG]](https://msdn.microsoft.com/library/7fd7ec40-deec-4c06-9493-1bc06b349682%28Office.15%29.aspx)
  
> Handles message and attachment objects.
    
[[MS-OXRTFCP]](https://msdn.microsoft.com/library/65dfe2df-1b69-43fc-8ebd-21819a7463fb%28Office.15%29.aspx)
  
> Encodes and decodes a compressed stream in RTF message bodies.
    
[[MS-OXRTFEX]](https://msdn.microsoft.com/library/411d0d58-49f7-496c-b8c3-5859b045f6cf%28Office.15%29.aspx)
  
> Encapsulates additional content formats (such as HTML) within the RTF body property of messages and attachments.
    
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

