---
title: "ShapePlowCode Cell (Shape Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm900
 
ms.localizationpriority: medium
ms.assetid: acf07fd7-6aa6-1a92-9b7a-bd6fea8a7cb2
description: "Determines whether this placeable shape moves away when you drop another placeable shape near this shape on the drawing page."
---

# ShapePlowCode Cell (Shape Layout Section)

Determines whether this placeable shape moves away when you drop another placeable shape near this shape on the drawing page.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Plow as page specifies. |**visSLOPlowDefault** <br/> |
|1  <br/> |Plow no shapes. |**visSLOPlowNever** <br/> |
|2  <br/> |Plow every shape. |**visSLOPlowAlways** <br/> |
   
## Remarks

You can also set the value of this cell for a particular shape on the **Placement** tab in the **Behavior** dialog box (with a shape selected, on the [Developer](run-in-developer-mode-display-the-developer-tab.md) tab, in the **Shape Design** group, click **Behavior**, and then click the **Placement** tab). 
  
To set this behavior for  *all*  the shapes on the drawing page, use the PlowCode cell in the Page Layout section. 
  
To get a reference to the ShapePlowCode cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |ShapePlowCode  <br/> |
   
To get a reference to the ShapePlowCode cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowShapeLayout** <br/> |
|**Cell index:**  <br/> |**visSLOPlowCode** <br/> |
   

