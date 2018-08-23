---
title: "PidTagWizardNoPabPage Canonical Property"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- MAPI.PidTagWizardNoPabPage
api_type:
- COM
ms.assetid: 9cec22cd-798d-41f6-9ebd-c7354f2162c2
description: "Last modified: March 09, 2015"
---

# PidTagWizardNoPabPage Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
This property contains TRUE if the profile wizard is to suppress the personal address book (PAB) page.
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_WIZARD_NO_PAB_PAGE  <br/> |
|Identifier:  <br/> |0x6701  <br/> |
|Data type:  <br/> |PT_BOOLEAN  <br/> |
|Area:  <br/> |Exchange Administrative  <br/> |
   
## Remarks

Service providers can set this property when calling a function based on the [LAUNCHWIZARDENTRY](launchwizardentry.md) function prototype. This property tells the profile wizard that the provider does not want the PAB page to be displayed during the user dialog. 
  
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

