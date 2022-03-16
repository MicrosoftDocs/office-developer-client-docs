---
title: "Invisible Cell (Shape Data Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251341
 
ms.localizationpriority: medium
ms.assetid: 5f368c2e-2a40-38ee-3568-ed5c57633345
description: "Specifies whether the shape data item is visible in the Shape Data window."
---

# Invisible Cell (Shape Data Section)

Specifies whether the shape data item is visible in the **Shape Data** window. 
  
|**Value**|**Description**|
|:-----|:-----|
| TRUE  <br/> | Shape data item is not visible. |
| FALSE  <br/> | Shape data item is visible. |
   
## Remarks

The value in this cell corresponds to the **Hidden** check box in the **Define Shape Data** dialog box (right-click the shape, point to **Data**, and then click **Define Shape Data**).
  
To get a reference to the Invisible cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Prop.  *name*  .Invisible where Prop.  *name*  is the row name  <br/> |
   
To get a reference to the Invisible cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionProp** <br/> |
| **Row index:**  <br/> |**visRowProp** +  *i*  where  *i*  = 0, 1, 2... |
| **Cell index:**  <br/> |**visCustPropsInvis** <br/> |
   

