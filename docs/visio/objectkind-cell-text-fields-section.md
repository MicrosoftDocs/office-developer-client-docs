---
title: "ObjectKind Cell (Text Fields Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm60058
 
ms.localizationpriority: medium
ms.assetid: cc4c373c-f073-e3c9-3aaa-a4abf050cd20

description: "Indicates the type of text field."
---

# ObjectKind Cell (Text Fields Section)

Indicates the type of text field.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
| 0  <br/> | Standard  <br/> |**visTFOKStandard** <br/> |
| 1  <br/> |Horizontal in vertical  <br/> |**visTFOKHorizontaInVertical** <br/> |
   
## Remarks

Text fields can be one of the following types:
  
- Standard, indicating that the field was inserted by field category.
    
- Horizontal in vertical, indicating that the field is horizontal text set within vertical text.
    
To get a reference to the ObjectKind cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Fields.ObjectKind[  *i*  ]            where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the ObjectKind cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionTextField** <br/> |
| Row index:  <br/> |**visRowField** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visFieldObjectKind** <br/> |
   

