---
title: "PidLidBusinessCardCardPicture Canonical Property"
description: Outlines the PidLidBusinessCardCardPicture canonical property, which contains the image to use on a business card.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidLidBusinessCardCardPicture
api_type:
- COM
ms.assetid: 2c7af147-f7eb-41ef-8403-93584a2041ba
---

# PidLidBusinessCardCardPicture Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the image to use on a business card.
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |dispidBCCardPicture  <br/> |
|Property set:  <br/> |PSETID_Address  <br/> |
|Long ID (LID):  <br/> |0x00008041  <br/> |
|Data type:  <br/> |PT_BINARY  <br/> |
|Area:  <br/> |Contact  <br/> |
   
## Remarks

The value of this property must be either a portable network graphics (PNG) or JPEG stream. This property should be used in conjunction with the **dispidBCDisplayDefinition** ([PidLidBusinessCardDisplayDefinition](pidlidbusinesscarddisplaydefinition-canonical-property.md)) property as follows: **dispidBCCardPicture** should not be present on a contact if **dispidBCDisplayDefinition** is not present. This property also should not be present if the data in **dispidBCCardPicture** does not require a card image. 
  
## Related resources

### Protocol specifications

[[MS-OXPROPS]](https://msdn.microsoft.com/library/f6ab1613-aefe-447d-a49c-18217230b148%28Office.15%29.aspx)
  
> Provides property set definitions and references to related Exchange Server protocol specifications.
    
[[MS-OXOCNTC]](https://msdn.microsoft.com/library/9b636532-9150-4836-9635-9c9b756c9ccf%28Office.15%29.aspx)
  
> Specifies the properties and operations that are permissible for contacts and personal distribution lists.
    
### Header files

Mapidefs.h
  
> Provides data type definitions.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

