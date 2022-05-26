---
title: "PidTagLanguages Canonical Property"
description: Outlines the PidTagLanguages canonical property, which contains an ASCII list of the languages that are incorporated in a message.
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagLanguages
api_type:
- HeaderDef
ms.assetid: 16d4e92d-d48e-4e06-9886-2d21f3d10640
---

# PidTagLanguages Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains an ASCII list of the languages that are incorporated in a message. 
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_LANGUAGES, PR_LANGUAGES_A, PR_LANGUAGES_W  <br/> |
|Identifier:  <br/> |0x002F  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

These properties contain a sequence of two-character country/region codes that are separated by commas. 
  
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

