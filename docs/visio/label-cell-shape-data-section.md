---
title: "Label Cell (Shape Data Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm510
 
ms.localizationpriority: medium
ms.assetid: 6d328b1c-8d92-eb1a-7317-7dd85c674ff9
description: "Specifies the label that appears to users in the Shape Data window. A label consists of alphanumeric characters, including the underscore (_) character."
---

# Label Cell (Shape Data Section)

Specifies the label that appears to users in the **Shape Data** window. A label consists of alphanumeric characters, including the underscore (_) character. 
  
## Remarks

The application automatically encloses the Label string in quotation marks in the cell, but the quotation marks are not displayed in the **Shape Data** window. 
  
If no label text is found, Visio displays the row name (Prop.Row) in the **Shape Data** window. 
  
To get a reference to the Label cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Prop. *Name*  .Label where Prop.  *Name*  is the row name  <br/> |
   
To get a reference to the Label cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionProp** <br/> |
|Row index:  <br/> |**visRowProp** +  *i*  where  *i*  = 0, 1, 2...  <br/> |
|Cell index:  <br/> |**visCustPropsLabel** <br/> |
   

