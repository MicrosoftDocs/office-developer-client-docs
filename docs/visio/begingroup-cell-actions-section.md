---
title: "BeginGroup Cell (Actions Section)"
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60022
ms.localizationpriority: medium
ms.assetid: 1ae7f629-fb9f-1a11-1194-b381d6c9de5b
description: "Indicates whether a separator is inserted into the menu above this action."
---

# BeginGroup Cell (Actions Section)

Indicates whether a separator is inserted into the menu above this action. 
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |A separator is inserted into the menu above this action. |
|FALSE  <br/> |A separator is not inserted into the menu above this action (the default). |
   
## Remarks

To get a reference to the BeginGroup cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |Actions. *name*.BeginGroup where Actions. *name* is the name of the Actions row  <br/> |
   
To get a reference to the BeginGroup cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionAction** <br/> |
|**Row index:**  <br/> |**visRowAction** +  *i*           where  *i*  = 0, 1, 2... |
|**Cell index:**  <br/> |**visActionBeginGroup** <br/> |
   

