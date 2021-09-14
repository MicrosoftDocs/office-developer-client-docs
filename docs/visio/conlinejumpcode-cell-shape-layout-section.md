---
title: "ConLineJumpCode Cell (Shape Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251652
 
ms.localizationpriority: medium
ms.assetid: af85588e-8e83-5168-7a8c-d7e8b4af5c27
description: "Determines when a connector jumps."
---

# ConLineJumpCode Cell (Shape Layout Section)

Determines when a connector jumps.
  
|**Value**|**Description**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |As page specifies; on the **Design** tab, click the arrow in the **Page Setup** group, and then click the **Layout and Routing** tab to see the page specifications  <br/> |**visSLOJumpDefault** <br/> |
|1  <br/> |Never  <br/> |**visSLOJumpNever** <br/> |
|2  <br/> |Always  <br/> |**visSLOJumpAlways** <br/> |
|3  <br/> |Other connector jumps  <br/> |**visSLOJumpOther** <br/> |
|4  <br/> |Neither connector jumps  <br/> |**visSLOJumpNeither** <br/> |
   
## Remarks

You can also set the value of this cell by selecting a dynamic connector, clicking **Behavior** in the **Shape Design** group on the [Developer](run-in-developer-mode-display-the-developer-tab.md) tab, and then clicking the **Connector** tab. 
  
To get a reference to the ConLineJumpCode cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |ConLineJumpCode  <br/> |
   
To get a reference to the ConLineJumpCode cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowShapeLayout** <br/> |
|Cell index:  <br/> |**visSLOJumpCode** <br/> |
   

