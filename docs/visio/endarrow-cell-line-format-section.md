---
title: "EndArrow Cell (Line Format Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm320
 
ms.localizationpriority: medium
ms.assetid: 2f9c11ba-a316-bc34-60d4-0a41b2af486f
description: "Indicates whether a line has an arrowhead or other line end format at its last vertex."
---

# EndArrow Cell (Line Format Section)

Indicates whether a line has an arrowhead or other line end format at its last vertex.
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |No arrowhead. |
|1 - 45  <br/> |Assorted arrowhead styles that correspond to indexed entries in the **Line** dialog box. |
   
## Remarks

You can also set this value in the **Line** dialog box (on the **Home** tab, in the **Shape** group, click **Line**, point to **Arrows**, and then click **More Arrows**). The size of the arrowhead is set in the EndArrowSize cell.
  
You can specify a custom line end using the USE function in this cell. 
  
To get a reference to the EndArrow cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |EndArrow  <br/> |
   
To get a reference to the EndArrow cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowLine** <br/> |
|**Cell index:**  <br/> |**visLineEndArrow** <br/> |
   

