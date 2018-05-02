---
title: "PidTagFormCategorySub Canonical Property"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
ms.prod: office-online-server
localization_priority: Normal
api_name:
- PidTagFormCategorySub
api_type:
- HeaderDef
ms.assetid: 0e654152-c850-417a-8877-29d47cf85db5
description: "Last modified: March 09, 2015"
---

# PidTagFormCategorySub Canonical Property

 **Last modified:** March 09, 2015 
  
 * **Applies to:** Outlook * 
  
Contains the subcategory of a form, as defined by a client application. 
  
|||
|:-----|:-----|
|Associated properties:  <br/> |PR_FORM_CATEGORY_SUB, PR_FORM_CATEGORY_SUB_A, PR_FORM_CATEGORY_SUB_W  <br/> |
|Identifier:  <br/> |0x3305  <br/> |
|Data type:  <br/> |PT_STRING8, PT_UNICODE  <br/> |
|Area:  <br/> |MAPI common  <br/> |
   
## Remarks

These properties are subordinate to the main form category that is provided in the **PR_FORM_CATEGORY** ( [PidTagFormCategory](pidtagformcategory-canonical-property.md)) property. 
  
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

