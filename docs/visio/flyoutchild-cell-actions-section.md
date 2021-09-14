---
title: "FlyoutChild Cell (Actions Section)"
 
 
manager: soliver
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm80003
 
ms.localizationpriority: medium
ms.assetid: b2405457-843c-0d46-5f4f-9c413826c3f1
description: "Determines whether the row is a child flyout menu of the last row above it that is not a flyout child."
---

# FlyoutChild Cell (Actions Section)

Determines whether the row is a child flyout menu of the last row above it that is not a flyout child. 
  
## Remarks

To get a reference to the FlyoutChild cell by name from another formula, or from a program by using the **CellsU** property, use the following. 
  
|||
|:-----|:-----|
|Cell name:  <br/> |Actions. *name*  .FlyoutChildwhere Actions.  *name*  is the name of the Actions row  <br/> |
   
To get a reference to the FlyoutChild cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
|||
|:-----|:-----|
|Section index:  <br/> |**visSectionAction** <br/> |
|Row index:  <br/> |**visRowAction** +  *i*  where  *i*  = 0, 1, 2...  <br/> |
|Cell index:  <br/> |**visActionFlyoutChild** <br/> |
   

