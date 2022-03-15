---
title: "Frame Cell (Hyperlinks Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm405
 
ms.localizationpriority: medium
ms.assetid: f71d8737-92ef-1124-ba4a-b7e17305bd0a

description: "Represents the name of a frame to target when the application is open as an Active document in a container application. The default is an empty string."
---

# Frame Cell (Hyperlinks Section)

Represents the name of a frame to target when the application is open as an Active document in a container application. The default is an empty string.
  
## Remarks

To get a reference to the Frame cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
| **Cell name:**  <br/> | Hyperlink.  *name*  .Frame            where Hyperlink.  *name*  is the row name  <br/> |
   
To get a reference to the Frame cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
| **Section index:**  <br/> |**visSectionHyperlink** <br/> |
| **Row index:**  <br/> |**visRow1stHyperlink** +  *i*            where  *i*  = 0, 1, 2... |
| **Cell index:**  <br/> |**visHLinkFrame** <br/> |
   

