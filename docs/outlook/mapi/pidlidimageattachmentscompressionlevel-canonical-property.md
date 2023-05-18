---
title: "PidLidImageAttachmentsCompressionLevel Canonical Property"
description: Outlines the PidLidImageAttachmentsCompressionLevel canonical property, which defines a compression level to apply on image attachments.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidImageAttachmentsCompressionLevel
api_type:
- COM
ms.assetid: cc169ba8-e9b7-42ad-8f0e-77b0843f95ea
---

# PidLidImageAttachmentsCompressionLevel Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Defines a compression level to apply on image attachments.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |dispidImgAttchmtsCompressLevel  <br/> |
|Property set:  <br/> |PSETID_Common  <br/> |
|Long ID (LID):  <br/> |0x00008593  <br/> |
|Data type:  <br/> |PT_LONG  <br/> |
|Area:  <br/> |Run-time configuration  <br/> |
   
## Remarks

The following are valid compression levels:
  
```cpp
enum PictureCompressLevel
{
 pclOriginal = 0,
 pclEmail = 1,
 pclWeb = 2,
 pclDocuments = 3,
};
```

## Related resources

### Protocol specifications

[[MS-OXPROPS]] 
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

