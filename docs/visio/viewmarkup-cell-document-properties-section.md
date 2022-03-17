---
title: "ViewMarkup Cell (Document Properties Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm1030802
 
ms.localizationpriority: medium
ms.assetid: 6c956266-8266-3312-5a68-cc9d8bdb8cd9
description: "Determines whether markup appears in the drawing window."
---

# ViewMarkup Cell (Document Properties Section)

Determines whether markup appears in the drawing window. 
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Markup is displayed on the drawing. |
|FALSE  <br/> |Markup is not displayed (the default). |
   
## Remarks

 When markup tracking is turned on (AddMarkup cell is TRUE), the ViewMarkup cell is automatically set to TRUE and remains TRUE even after markup tracking has been turned off (AddMarkup cell is FALSE). The value in the ViewMarkup cell is ignored when the AddMarkup cell is TRUE. 
  
The ViewMarkup cell is also set to TRUE when comments are inserted in a drawing (whether or not markup tracking is turned on) and must be TRUE to see comments in the drawing.
  
This cell corresponds to the **Show Markup** command in the **Markup** group on the **Review** tab. 
  
To get a reference to the ViewMarkup cell by name from another formula, or from a program by using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |ViewMarkup  <br/> |
   
To get a reference to the ViewMarkup cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowDoc** <br/> |
|**Cell index:**  <br/> |**visDocViewMarkup** <br/> |
   

