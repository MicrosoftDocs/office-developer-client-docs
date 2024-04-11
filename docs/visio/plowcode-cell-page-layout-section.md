---
title: "PlowCode Cell (Page Layout Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251660
 
ms.localizationpriority: medium
ms.assetid: e43f3d29-7def-d36e-ac64-62f0a389d415
description: "Determines whether placeable shapes move away when you drop a placeable shape near another placeable shape on the drawing page."
---

# PlowCode Cell (Page Layout Section)

Determines whether placeable shapes move away when you drop a placeable shape near another placeable shape on the drawing page.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Don't move shapes  <br/> |**visPLOPlowNone** <br/> |
|1  <br/> |Move shapes  <br/> |**visPLOPlowAll** <br/> |
   
## Remarks

You can also set the value of this cell on the **Layout and Routing** tab in the **Page Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow) by using the **Move other shapes away on drop** check box. 
  
To get a reference to the PlowCode cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |PlowCode  <br/> |
   
To get a reference to the PlowCode cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowPageLayout** <br/> |
|**Cell index:**  <br/> |**visPLOPlowCode** <br/> |
   

