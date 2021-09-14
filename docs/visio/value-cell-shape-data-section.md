---
title: "Value Cell (Shape Data Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm1090
 
ms.localizationpriority: medium
ms.assetid: fd42a6ce-f621-4e9e-aba3-23a1b87a5651
description: "Contains the shape data item's value as entered in the Define Shape Data dialog box."
---

# Value Cell (Shape Data Section)

Contains the shape data item's value as entered in the **Define Shape Data** dialog box. 
  
## Remarks

Formulas entered in this cell are overridden by values entered in the **Define Shape Data** dialog box. This is true even if you use the GUARD function to protect the formula. 
  
To get a reference to the Value cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | Prop.  *Name*  .Value where Prop.  *Name*  is the row name  <br/> |
   
To get a reference to the Value cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionProp** <br/> |
| Row index:  <br/> |**visRowProp** +  *i*  where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visCustPropsValue** <br/> |
   

