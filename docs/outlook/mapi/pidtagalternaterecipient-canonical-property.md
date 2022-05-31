---
title: "PidTagAlternateRecipient Canonical Property"
description: Outlines the PidTagAlternateRecipient canonical property, which contains a list of entry identifiers for alternate recipients.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagAlternateRecipient
api_type:
- HeaderDef
ms.assetid: df787b60-2f53-42ac-89b5-1b52c906f472
---

# PidTagAlternateRecipient Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains a list of entry identifiers for alternate recipients designated by the original recipient. 
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_ALTERNATE_RECIPIENT  <br/> |
|Identifier:  <br/> |0x3A01  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Address  <br/> |
   
## Remarks

This property is used for auto forwarded messages. It contains a [FLATENTRYLIST](flatentrylist.md) structure of alternate recipients. If autoforwarding is not permitted or if no alternate recipient has been designated, a nondelivery report is generated. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides references to related Exchange Server protocol specifications.
    
[[MS-OXCFXICS]](https://msdn.microsoft.com/library/b9752f3d-d50d-44b8-9e6b-608a117c8532%28Office.15%29.aspx)
  
> Handles the order and flow for data transfers between a client and server.
    
[[MS-OXCICAL]](https://msdn.microsoft.com/library/a685a040-5b69-4c84-b084-795113fb4012%28Office.15%29.aspx)
  
> Converts between IETF RFC2445, RFC2446, and RFC2447, and appointment and meeting objects.
    
[[MS-OXTNEF]](https://msdn.microsoft.com/library/1f0544d7-30b7-4194-b58f-adc82f3763bb%28Office.15%29.aspx)
  
> Encodes and decodes message and attachment objects to an efficient stream representation.
    
### Header files

Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
Mapidefs.h
  
> Provides data type definitions.
    
## See also



[FLATENTRYLIST](flatentrylist.md)


[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

