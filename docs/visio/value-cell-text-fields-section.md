---
title: "Value Cell (Text Fields Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1095
 
ms.localizationpriority: medium
ms.assetid: 3ca662c8-1ce4-89a9-3264-1ba533fcd444
description: "Contains the function for a field."
---

# Value Cell (Text Fields Section)

Contains the function for a field.
  
## Remarks

You can set the value of this cell using the **Field** dialog box (on the **Insert** tab, in the **Text** group, click **Field**).
  
To get a reference to the Value cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Fields.Value[ *i*  ] where  *i*  = <1>, 2, 3... |
   
To get a reference to the Value cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionTextField** <br/> |
|**Row index:**  <br/> |**visRowField** +  *i*  where  *i*  = 0, 1, 2... |
|**Cell index:**  <br/> |**visFieldCell** <br/> |
   

