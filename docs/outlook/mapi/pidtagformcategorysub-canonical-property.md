---
title: "PidTagFormCategorySub Canonical Property"
description: Outlines the PidTagFormCategorySub canonical property, which contains the subcategory of a form, as defined by a client application. 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
ms.service: office-online-server
ms.localizationpriority: medium
api_name:
- PidTagFormCategorySub
api_type:
- HeaderDef
ms.assetid: 0e654152-c850-417a-8877-29d47cf85db5
---

# PidTagFormCategorySub Canonical Property

  
  
**Applies to**: Outlook 2013 | Outlook 2016 
  
Contains the subcategory of a form, as defined by a client application. 
  
|Property|Value|
|:-----|:-----|
|Associated properties:  <br/> |PR_FORM_CATEGORY_SUB, PR_FORM_CATEGORY_SUB_A, PR_FORM_CATEGORY_SUB_W  <br/> |
|Identifier:  <br/> |0x3305  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI common  <br/> |
   
## Remarks

These properties are subordinate to the main form category that is provided in the **PR_FORM_CATEGORY** ([PidTagFormCategory](pidtagformcategory-canonical-property.md)) property. 
  
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

