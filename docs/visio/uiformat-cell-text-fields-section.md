---
title: "UIFormat Cell (Text Fields Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1080
 
ms.localizationpriority: medium
ms.assetid: 0dddef20-c58e-2306-ab8e-6cac8e159f61

description: "Determines the format of an inserted field in versions of Visio earlier than Visio 2000."
---

# UIFormat Cell (Text Fields Section)

Determines the format of an inserted field in versions of Visio earlier than Visio 2000.
  
## Remarks

This cell does not appear in the ShapeSheet window. Use this cell if you need to deal with backward capability issues, such as saving a Visio version 2000 drawing in Visio version 5.0 file format.
  
To get a reference to the UIFormat cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Fields.UIFmt[  *i*  ]            where  *i*  = <1>, 2, 3...  <br/> |
   
To get a reference to the UIFormat cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionTextField** <br/> |
| Row index:  <br/> |**visRowField** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visFieldUIFormat** <br/> |
   

