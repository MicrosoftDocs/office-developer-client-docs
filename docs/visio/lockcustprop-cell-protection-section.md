---
title: "LockCustProp Cell (Protection Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm60055
 
ms.localizationpriority: medium
ms.assetid: d1c23f1d-485d-a897-594d-15d6e8d0fb3c
description: "Determines whether the user can add, delete, or modify shape data in the user interface (UI) by using the Define Shape Data dialog box or the shortcut menu for the Shape Data window."
---

# LockCustProp Cell (Protection Section)

Determines whether the user can add, delete, or modify shape data in the user interface (UI) by using the **Define Shape Data** dialog box or the shortcut menu for the **Shape Data** window. 
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |The **Define Shape Data** command on the shortcut menu in the **Shape Data** window is disabled.  <br/> |
|FALSE  <br/> |The **Define Shape Data** command on the shortcut menu in the **Shape Data** window is enabled (the default).  <br/> |
   
## Remarks

A value of TRUE does not prevent a user from changing the value of a shape data item or changing the Shape Data section in the ShapeSheet window. 
  
To get a reference to the LockCustProp cell by name from another formula, or from a program using the **CellsU** property, use: 
  
|||
|:-----|:-----|
|Cell name:  <br/> |LockCustProp  <br/> |
   
To get a reference to the LockCustProp cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionObject** <br/> |
|Row index:  <br/> |**visRowLock** <br/> |
|Cell index:  <br/> |**visLockCustProp** <br/> |
   

