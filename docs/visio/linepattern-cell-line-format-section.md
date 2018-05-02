---
title: "LinePattern Cell (Line Format Section)"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm560
 
localization_priority: Normal
ms.assetid: a416762b-7294-c99f-d9f1-332c3ed35dff
description: "Determines the line pattern of the shape. The value entered in the LinePattern cell is a number that is an index into a collection of line patterns."
---

# LinePattern Cell (Line Format Section)

Determines the line pattern of the shape. The value entered in the LinePattern cell is a number that is an index into a collection of line patterns.
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |No line pattern  <br/> |
|1  <br/> |Solid  <br/> |
|2 - 23  <br/> |Assorted line patterns  <br/> |
   
## Remarks

You can view the line pattern collection in the **Line** dialog box (on the **Home** tab, in the **Shape** group, click **Line**, point to **Dashes**, and then click **More Lines**).
  
To specify a custom line pattern, use the USE function in this cell.
  
To get a reference to the LinePattern cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |LinePattern  <br/> |
   
To get a reference to the LinePattern cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowLine** <br/> |
|Cell index:  <br/> |**visLinePattern** <br/> |
   

