---
title: "PidTagLanguages Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagLanguages
api_type:
- HeaderDef
ms.assetid: 16d4e92d-d48e-4e06-9886-2d21f3d10640
description: "Last modified: March 09, 2015"
---

# PidTagLanguages Canonical Property

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Contains an ASCII list of the languages that are incorporated in a message. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_LANGUAGES, PR_LANGUAGES_A, PR_LANGUAGES_W  <br/> |
|Identifier:  <br/> |0x002F  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |General messaging  <br/> |
   
## Remarks

These properties contain a sequence of two-character country/region codes that are separated by commas. 
  
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

