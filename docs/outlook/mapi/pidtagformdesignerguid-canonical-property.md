---
title: "PidTagFormDesignerGuid Canonical Property"
description: Outlines the PidTagFormDesignerGuid canonical property, which contains the unique identifier for the object that is used to design a form.
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagFormDesignerGuid
api_type:
- HeaderDef
ms.assetid: 8d7f5789-610c-47f6-a109-5513d677ef60
---

# PidTagFormDesignerGuid Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the unique identifier for the object that is used to design a form.
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_FORM_DESIGNER_GUID  <br/> |
|Identifier:  <br/> |0x3309  <br/> |
|Data type:  <br/> |PT_GUID  <br/> |
|Area:  <br/> |MAPI common  <br/> |
   
## Remarks

This property usually contains the globally unique identifier (GUID) of the design program that is used to create the form. This property can be empty. 
  
The [MAPIUID](mapiuid.md) structure contains the definition of the unique identifier. 
  
## Related resources

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

