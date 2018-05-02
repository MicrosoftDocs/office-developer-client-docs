---
title: "Value Cell (User-Defined Cells Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1100
 
localization_priority: Normal
ms.assetid: 495b2aec-e197-75eb-9974-e7c92d26546f

description: "Specifies a value for the corresponding user-defined cell."
---

# Value Cell (User-Defined Cells Section)

Specifies a value for the corresponding user-defined cell.
  
## Remarks

To refer to this value in another cell, specify the user-defined name entered in the row label User.Row.
  
To get a reference to the Value cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | User.  *Name*  .Value            where User.  *Name*  is the row name  <br/> |
   
To get a reference to the Value cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionUser** <br/> |
| Row index:  <br/> |**visRowUser** +  *i*            where  *i*  = 0, 1, 2...  <br/> |
| Cell index:  <br/> |**visUserValue** <br/> |
   

