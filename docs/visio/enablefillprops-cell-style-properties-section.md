---
title: "EnableFillProps Cell (Style Properties Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- Vis_DSS.chm300
 
ms.localizationpriority: medium
ms.assetid: 2b3334de-588c-6cf3-bc88-be03ae71b1a6
description: "Determines whether a style includes fill properties."
---

# EnableFillProps Cell (Style Properties Section)

Determines whether a style includes fill properties.
  
|**Value**|**Description**|
|:-----|:-----|
|TRUE  <br/> |Include fill properties. |
|FALSE  <br/> |Exclude fill properties. |
   
## Remarks

To get a reference to the EnableFillProps cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |EnableFillProps  <br/> |
   
To get a reference to the EnableFillProps cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowStyle** <br/> |
|**Cell index:**  <br/> |**visStyleIncludesFill** <br/> |
   

