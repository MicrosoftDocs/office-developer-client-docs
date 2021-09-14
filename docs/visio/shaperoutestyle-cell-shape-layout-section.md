---
title: "ShapeRouteStyle Cell (Shape Layout Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm905
 
ms.localizationpriority: medium
ms.assetid: a5dcd2e0-e343-5ee2-2b63-2a1312437901
description: "Determines the routing style and direction for a selected connector on the drawing page."
---

# ShapeRouteStyle Cell (Shape Layout Section)

Determines the routing style and direction for a selected connector on the drawing page.
  
|**Value**|**Routing style**|**Direction**|**Automation constant**|
|:-----|:-----|:-----|:-----|
|0  <br/> |Use page default  <br/> |None  <br/> |**visLORouteDefault** <br/> |
|1  <br/> |Right angle  <br/> |None  <br/> |**visLORouteRightAngle** <br/> |
|2  <br/> |Straight  <br/> |None  <br/> |**visLORouteStraight** <br/> |
|3  <br/> |Organization chart  <br/> |Top to bottom  <br/> |**visLORouteOrgChartNS** <br/> |
|4  <br/> |Organization chart  <br/> |Left to right  <br/> |**visLORouteOrgChartWE** <br/> |
|5  <br/> |Flowchart  <br/> |Top to bottom  <br/> |**visLORouteFlowchartNS** <br/> |
|6  <br/> |Flowchart  <br/> |Left to right  <br/> |**visLORouteFlowchartWE** <br/> |
|7  <br/> |Tree  <br/> |Top to bottom  <br/> |**visLORouteTreeNS** <br/> |
|8  <br/> |Tree  <br/> |Left to right  <br/> |**visLORouteTreeWE** <br/> |
|9  <br/> |Network  <br/> |None  <br/> |**visLORouteNetwork** <br/> |
|10  <br/> |Organization chart  <br/> |Bottom to top  <br/> |**visLORouteOrgChartSN** <br/> |
|11  <br/> |Organization chart  <br/> |Right to left  <br/> |**visLORouteOrgChartEW** <br/> |
|12  <br/> |Flowchart  <br/> |Bottom to top  <br/> |**visLORouteFlowchartSN** <br/> |
|13  <br/> |Flowchart  <br/> |Right to left  <br/> |**visLORouteFlowchartEW** <br/> |
|14  <br/> |Tree  <br/> |Bottom to top  <br/> |**visLORouteTreeSN** <br/> |
|15  <br/> |Tree  <br/> |Right to left  <br/> |**visLORouteTreeEW** <br/> |
|16  <br/> |Center to center  <br/> |None  <br/> |**visLORouteCenterToCenter** <br/> |
|17  <br/> |Simple  <br/> |Top to bottom  <br/> |**visLORouteSimpleNS** <br/> |
|18  <br/> |Simple  <br/> |Left to right  <br/> |**visLORouteSimpleWE** <br/> |
|19  <br/> |Simple  <br/> |Bottom to top  <br/> |**visLORouteSimpleSN** <br/> |
|20  <br/> |Simple  <br/> |Right to left  <br/> |**visLORouteSimpleEW** <br/> |
|21  <br/> |Simple horizontal-vertical  <br/> |None  <br/> |**visLORouteSimpleHV** <br/> |
|22  <br/> |Simple vertical-horizontal  <br/> |None  <br/> |**visLORouteSimpleVH** <br/> |
   
## Remarks

You can also set the value of this cell for a particular connector on the **Connector** tab in the **Behavior** dialog box (with a connector selected, click **Behavior** on the [Developer](run-in-developer-mode-display-the-developer-tab.md) tab, and then click the **Connector** tab). 
  
To set this behavior for  *all*  the connectors on a page, use the RouteStyle cell in the Page Layout section. 
  
In versions earlier than Visio 2000, you set this behavior using the ObjBehavior cell in the Miscellaneous section.
  
To get a reference to the ShapeRouteStyle cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |ShapeRouteStyle  <br/> |
   
To get a reference to the ShapeRouteStyle cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowShapeLayout** <br/> |
|Cell index:  <br/> |**visSLORouteStyle** <br/> |
   

