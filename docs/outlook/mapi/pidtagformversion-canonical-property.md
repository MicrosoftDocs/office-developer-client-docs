---
title: "PidTagFormVersion Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagFormVersion
api_type:
- HeaderDef
ms.assetid: f2220060-65ea-4969-88d7-8348bd5aa242
description: "Last modified: March 09, 2015"
---

# PidTagFormVersion Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the version of a form. 
  
|Property |Value |
|:-----|:-----|
|Associated properties:  <br/> |PR_FORM_VERSION, PR_FORM_VERSION_A, PR_FORM_VERSION_W  <br/> |
|Identifier:  <br/> |0x3301  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI common  <br/> |
   
## Remarks

These properties indicate what design version is currently in effect for the form. The version is defined and maintained by the form's designer and is not necessarily related to any MAPI component version. 
  
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

