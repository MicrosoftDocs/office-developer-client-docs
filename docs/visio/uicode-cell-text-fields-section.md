---
title: "UICode Cell (Text Fields Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm1075
 
ms.localizationpriority: medium
ms.assetid: 1d9717c1-4310-0d62-874f-4df77cd81627

description: "Determines the code of an inserted field in versions of Visio earlier than Visio 2000."
---

# UICode Cell (Text Fields Section)

Determines the code of an inserted field in versions of Visio earlier than Visio 2000.
  
## Remarks

This cell does not appear in the ShapeSheet window. Use this cell if you need to deal with backward capability issues, such as saving a Visio version 2000 drawing in Visio version 5.0 file format.
  
To get a reference to the UICode cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Fields.UICod[  *i*  ]            where  *i*  = <1>, 2, 3... |
   
To get a reference to the UICode cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionTextField** <br/> |
| Row index:  <br/> |**visRowField** +  *i*            where  *i*  = 0, 1, 2... |
| Cell index:  <br/> |**visFieldUICode** <br/> |
   

