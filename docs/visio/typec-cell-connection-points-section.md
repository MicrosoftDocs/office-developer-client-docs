---
title: "Type / C Cell (Connection Points Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm82251723
 
ms.localizationpriority: medium
ms.assetid: 2264d026-2041-3855-2b23-553ce67ae69d

description: "Determines the connection point type."
---

# Type / C Cell (Connection Points Section)

Determines the connection point type.
  
|**Value**|**Type**|**Automation constant**|
|:-----|:-----|:-----|
|0  <br/> |Inward  <br/> |**visCnnctTypeInward** <br/> |
|1  <br/> |Outward  <br/> |**visCnnctTypeOutward** <br/> |
|2  <br/> |Inward &amp; Outward  <br/> |**visCnnctTypeInwardOutward** <br/> |
   
## Remarks

You can also set the connection point type by choosing the **Connector** tool, selecting a shape, and then right-clicking a connection point. To do this, you need to run in [developer](run-in-developer-mode-display-the-developer-tab.md) mode. 
  
To get a reference to the Type / C cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Connections.Type[  *i*  ]            where  *i*  = <1>, 2, 3... |
   
To get a reference to the Type / C cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionConnectionPts** <br/> |
|**Row index:**  <br/> |**visRowConnectionPts** +  *i*  where  *i*  = 0, 1, 2... |
|**Cell index:**  <br/> |**visCnnctType** (non-extended rows) **visCnnctC** (extended rows)  <br/> |
   
For information about non-extended and extended rows, see Connection Points row.
  

