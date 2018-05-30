---
title: "PidTagWizardNoPstPage Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagWizardNoPstPage
api_type:
- COM
ms.assetid: 1ac09578-892b-4c72-92f6-c2419ac2efe8
description: "Last modified: March 09, 2015"
---

# PidTagWizardNoPstPage Canonical Property

  
  
**Applies to**: Outlook 
  
This property contains TRUE if the profile wizard is to suppress the personal message store (PST) page.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_WIZARD_NO_PST_PAGE  <br/> |
|Identifier:  <br/> |0x6700  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Exchange Administrative  <br/> |
   
## Remarks

Service providers can set this property when calling a function based on the [LAUNCHWIZARDENTRY](launchwizardentry.md) function prototype. This property tells the profile wizard that the provider does not want the PST page to be displayed during the user dialog. 
  
## Related resources

### Header files

Mapidefs.h
  
> Provides data type definitions.
    
Mapitags.h
  
> Contains definitions of properties listed as associated properties.
    
## See also



[MAPI Properties](mapi-properties.md)
  
[MAPI Canonical Properties](mapi-canonical-properties.md)
  
[Mapping Canonical Property Names to MAPI Names](mapping-canonical-property-names-to-mapi-names.md)
  
[Mapping MAPI Names to Canonical Property Names](mapping-mapi-names-to-canonical-property-names.md)

