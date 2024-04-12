---
title: "QuickStyleVariation Cell (Quick Style Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: overview
 
ms.localizationpriority: medium
ms.assetid: e3b58a19-9f1a-4f2b-9fe2-45cbb7ec6898
description: "Determines whether to override the formulas and values of text, line, and fill color (or a combination of those properties) by using colors that contrast with the diagram background. Value is a bitwise OR of 0, 1, 2, 4, and 8."
---

# QuickStyleVariation Cell (Quick Style Section)

Determines whether to override the formulas and values of text, line, and fill color (or a combination of those properties) by using colors that contrast with the diagram background. Value is a bitwise OR of 0, 1, 2, 4, and 8.
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |Do not alter a shape's text, line, or fill color (or any combination of those properties) to remain visible against a theme's given background color. |
|1  <br/> |Do not alter a shape's text, line, or fill color (or any combination of those properties) to remain visible against a theme's given background color. |
|2  <br/> |Alter a shape's text color, if necessary, to remain visible against a theme's given background color. |
|4  <br/> |Alter a shape's line color, if necessary, to remain visible against a theme's given background color. |
|8  <br/> |Alter a shape's fill color, if necessary, to remain visible against a theme's given background color. |
   
## Remarks

Use the QuickStyleVariation cell to guarantee visibility in either text or lines when they are outside any visible shape geometry (for example, in a shape whose textbox is below the bottom of the shape, such as those in Network Diagrams). The cell's default value is 0, which means that its behavior is inactive. Any other value triggers the cell's behavior.
  
The QuickStyleVariation value overrides the value produced by the THEMEVAL function when it resides in the Color (Character Section), FillForegnd, or LineColor cells (or produced by direct references to these three properties by means of THEMEVAL("CharacterColor"), THEMEVAL("FillColor"), and THEMEVAL("LineColor")).
  
To get a reference to the **QuickStyleVariation** cell by name from another formula, by getting the value of the **N** attribute of a **Cell** element, or from a program by using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |QuickStyleVariation  <br/> |
   
To get a reference to the **QuickStyleVariation** cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowQuickStyleProperties** <br/> |
|**Cell index:**  <br/> |**visQuickStyleVariation** <br/> |
   

