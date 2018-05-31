---
title: "LockTextEdit Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm665
 
localization_priority: Normal
ms.assetid: d8de5fa4-826b-e869-4d9f-997361d05fd8
description: "Locks the text of a shape so that it cannot be edited."
---

# LockTextEdit Cell (Protection Section)

Locks the text of a shape so that it cannot be edited.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Text cannot be edited.  <br/> |
| FALSE  <br/> | Text can be edited.  <br/> |
   
## Remarks

You can still format text by applying a style in the **Text** dialog box (on the **Home** tab, click the **Font** arrow). 
  
To get a reference to the LockTextEdit cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
| Cell name:  <br/> | LockTextEdit  <br/> |
   
To get a reference to the LockTextEdit cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
| Section index:  <br/> |**visSectionObject** <br/> |
| Row index:  <br/> |**visRowLock** <br/> |
| Cell index:  <br/> |**visLockTextEdit** <br/> |
   

