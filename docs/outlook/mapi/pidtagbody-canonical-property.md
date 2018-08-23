---
title: "PidTagBody Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagBody
api_type:
- HeaderDef
ms.assetid: 47c0d0fe-4d57-4b81-bdb5-336de85c194c
description: "Last modified: March 09, 2015"
---

# PidTagBody Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the message text.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_BODY, PR_BODY_A, PR_BODY_W  <br/> |
|Identifier:  <br/> |0x1000  <br/> |
|Data type:  <br/> |PT_UNICODE, PT_STRING8  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

These properties are typically used only in an interpersonal message (IPM). 
  
Message stores that support Rich Text Format (RTF) ignore any changes to white space in the message text. When **PR_BODY** is stored for the first time, the message store also generates and stores the **PR_RTF_COMPRESSED** ([PidTagRtfCompressed](pidtagrtfcompressed-canonical-property.md)) property, the RTF version of the message text. If the [IMAPIProp::SaveChanges](imapiprop-savechanges.md) method is subsequently called and **PR_BODY** has been modified, the message store calls the [RTFSync](rtfsync.md) function to ensure synchronization with the RTF version. If only white space has been changed, the properties are left unchanged. This preserves any nontrivial RTF formatting when the message travels through non-RTF-aware clients and messaging systems. 
  
The value for this property must be expressed in the code page of the operating system that MAPI is running on. 
  
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



[PidTagRtfInSync Canonical Property](pidtagrtfinsync-canonical-property.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

