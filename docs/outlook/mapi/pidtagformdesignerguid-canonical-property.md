---
title: "PidTagFormDesignerGuid Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagFormDesignerGuid
api_type:
- HeaderDef
ms.assetid: 8d7f5789-610c-47f6-a109-5513d677ef60
description: "Last modified: March 09, 2015"
---

# PidTagFormDesignerGuid Canonical Property

  
  
**Applies to**: Outlook 
  
Contains the unique identifier for the object that is used to design a form.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_FORM_DESIGNER_GUID  <br/> |
|Identifier:  <br/> |0x3309  <br/> |
|Data type:  <br/> |PT_GUID  <br/> |
|Area:  <br/> |MAPI common  <br/> |
   
## Remarks

This property usually contains the globally unique identifier (GUID) of the design program that is used to create the form. This property can be empty. 
  
The [MAPIUID](mapiuid.md) structure contains the definition of the unique identifier. 
  
## Related Resources

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

