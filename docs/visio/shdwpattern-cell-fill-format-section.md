---
title: "ShdwPattern Cell (Fill Format Section)"
 
 
manager: lindalu
ms.date: 03/09/2015
ms.audience: Developer
ms.topic: reference
f1_keywords:
- vis_sdr.chm935
 
ms.localizationpriority: medium
ms.assetid: eca73b80-9835-9011-1dce-187ccee92e76
description: "Determines the fill pattern for a shape's shadow."
---

# ShdwPattern Cell (Fill Format Section)

Determines the fill pattern for a shape's shadow.
  
|**Value**|**Description**|
|:-----|:-----|
|0  <br/> |None (transparent fill)  <br/> |
|1  <br/> |Solid foreground color  <br/> |
|2 - 40  <br/> |Assorted patterns  <br/> |
   
## Remarks

To set the fill pattern, enter a number from 0 to 40, which is an index into a collection of patterns. You can view the fill pattern collection in the **Fill** dialog box (on the **Home** tab, in the **Shape** group, click **Fill**, and then click **Fill Options**).
  
To get a reference to the ShdwPattern cell by name from another formula, or from a program using the **CellsU** property, use: 
  
||Value |
|:-----|:-----|
|**Cell name:**  <br/> |ShdwPattern  <br/> |
   
To get a reference to the ShdwPattern cell by index from a program, use the **CellsSRC** property with the following arguments: 
  
||Value |
|:-----|:-----|
|**Section index:**  <br/> |**visSectionObject** <br/> |
|**Row index:**  <br/> |**visRowFill** <br/> |
|**Cell index:**  <br/> |**visFillShdwPattern** <br/> |
   

