---
title: "LineJumpCode Cell (Page Layout Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm540
 
localization_priority: Normal
ms.assetid: 56f9043d-a632-65df-c710-45867cce1627
description: "Determines the connectors to which you want to add jumps."
---

# LineJumpCode Cell (Page Layout Section)

Determines the connectors to which you want to add jumps.
  
|**Value**|**Connectors to which you want to add jumps**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |None  <br/> |**visPLOJumpNone** <br/> |
|1  <br/> |Horizontal lines  <br/> |**visPLOJumpHorizontal** <br/> |
|2  <br/> |Vertical lines  <br/> |**visPLOJumpVertical** <br/> |
|3  <br/> |Last routed line  <br/> |**visPLOJumpLastRouted** <br/> |
|4  <br/> |Last displayed line (top shape in the  *z*  -order)  <br/> |**visPLOJumpDisplayOrder** <br/> |
|5  <br/> |First displayed line (shape at the bottom of the  *z*  -order)  <br/> |**visPLOJumpReverseDisplayOrder** <br/> |
   
## Remarks

You can also set the value of this cell on the **Layout and Routing** tab in the **Page Setup** dialog box (on the **Design** tab, click the **Page Setup** arrow, and then click **Layout and Routing**).
  
To get a reference to the LineJumpCode cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |LineJumpCode  <br/> |
   
To get a reference to the LineJumpCode cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowPageLayout** <br/> |
|Cell index:  <br/> |**visPLOJumpCode** <br/> |
   

